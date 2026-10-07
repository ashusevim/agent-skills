# Send / draft / search recipes

## Send (Python)

```python
import base64
from email.message import EmailMessage
msg = EmailMessage()
msg.set_content("Body here")
msg["To"], msg["From"], msg["Subject"] = "to@x.com", "me@x.com", "Hi"
raw = base64.urlsafe_b64encode(msg.as_bytes()).decode()
service.users().messages().send(userId="me", body={"raw": raw}).execute()
```

## Send (cURL)

```
curl --request POST 'https://gmail.googleapis.com/gmail/v1/users/me/messages/send' \
  --header 'Authorization: Bearer ACCESS_TOKEN' \
  --header 'Content-Type: application/json' \
  --data '{"raw":"MESSAGE"}'   # RFC 2822 MIME, base64url
```

Drafts: same `raw`, wrapped `{"message": {"raw": …}}`, to `users/me/drafts`; send via `drafts.send`.

## Attachments

Multipart MIME (`add_attachment` in Python EmailMessage; MimeMultipart in Java), then same base64url + `raw` path. Large files: resumable `uploads` flow per the uploads guide.

## Search

```
GET https://www.googleapis.com/gmail/v1/users/me/messages?q=in:sent after:2014/01/01 before:2014/02/01
GET .../messages?q=from:boss@x.com has:attachment&labelIds[]=INBOX
```

- `q` = Gmail web search syntax. Dates = PST midnight; other zones → epoch seconds.
- `labelIds[]` narrows to system (`INBOX`, `SENT`) or user labels.
- Gotchas vs UI: no alias expansion (`from:` won't match sender aliases); no thread-wide search in API.
