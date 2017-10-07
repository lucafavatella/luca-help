## Protocols

### IMAP

https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol

https://en.wikipedia.org/wiki/Lemonade_Profile

[IMAP server tester](https://imapwiki.org/ImapTest)

### SMTP

TODO

## Minimal IMAP+SMTP client (with TLS)

### State of the art

[Emacs minimal IMAP client](https://github.com/legoscia/bic)

### Proposal

#### Must

*Safe concurrent* message deletion (IMAP EXPUNGE).
[Via IMAP UID EXPUNGE](https://github.com/k9mail/k-9/issues/2782#issuecomment-334943119) [considering UID as per-session](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Disadvantages).

#### Should

*Notification* of new message delivered in mailbox.
[Via IMAP IDLE](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Disadvantages) keeping TCP connection alive via either [canceling and restarting IDLE](https://stackoverflow.com/questions/2513194/imap-idle-timeout#2538941) or via [NOOP](https://www.isode.com/whitepapers/imap-idle.html).

#### Could

*Partial* fetch of email in MIME format.
[Via IMAP](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Access_to_MIME_message_parts_and_partial_fetch).

*Store* email *sent*.
Email sent via SMTP.
Store email [via Bcc and filtering fetch](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Disadvantages).

#### Won't

(Intentionally left blank for now.)

## Snippets

```
imapsync \
         --host1 HOST1               --user1 USER1 --passfile1 PASSFILE1 --ssl1 \
         --host2 HOST2 --port2 PORT2 --user2 USER2 --passfile2 PASSFILE2 --ssl2 \
         --prefix2 'Archive/' --folder 'MyFolder' \
         --justfoldersizes --dry \
         --showpasswords --timeout 5
```
