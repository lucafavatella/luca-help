## Protocols

### IMAP

https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol

https://en.wikipedia.org/wiki/Lemonade_Profile

### SMTP

TODO

## Software

### Client

[IMAP server tester](https://imapwiki.org/ImapTest)

[Minimal IMAP client for Emacs](https://github.com/legoscia/bic)

### Server

OpenBSD [exemplifies a mail server](https://www.openbsd.org/opensmtpd/faq/example1.html) as an SMTP server (OpenSMTPD) and an IMAP server (Dovecot).
> The mail server will be doing the following things:
> * Accepting mails for multiple domains and virtual users
> * Allowing virtual users to authenticate and send mail
> * Providing IMAP access for the virtual users
>
> ... a single system user named `vmail` is used for all virtual users.
>
> The home directory `/var/vmail` is used to store virtual users maildir folders, and is entirely managed by the IMAP server (Dovecot). Mail is delivered to Dovecot via LMTP ...
>
> Virtual users sending mail are authenticated via the `/etc/mail/passwd` file, which is shared with Dovecot for the IMAP authentication. 
>
> Virtual users access and read their mails via IMAP. Dovecot listens on a LMTP socket ... for mail delivery from `smtpd(8)`. Passwords are shared with `smtpd(8)` in the `/etc/mail/passwd` file and mails are delivered to `/var/vmail` subfolders.

[Full stack email server as Docker image](https://github.com/tomav/docker-mailserver), with Postfix as SMTP server and Dovecot as IMAP server. It has tests, written using Bats ("Bash Automated Testing System").

## Minimal IMAP+SMTP client (with TLS)

### Must

*Safe concurrent* message deletion (IMAP EXPUNGE).
[Via IMAP UID EXPUNGE](https://github.com/k9mail/k-9/issues/2782#issuecomment-334943119) [considering UID as per-session](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Disadvantages).

### Should

*Notification* of new message delivered in mailbox.
[Via IMAP IDLE](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Disadvantages) keeping TCP connection alive via either [canceling and restarting IDLE](https://stackoverflow.com/questions/2513194/imap-idle-timeout#2538941) or via [NOOP](https://www.isode.com/whitepapers/imap-idle.html).

### Could

*Partial* fetch of email in MIME format.
[Via IMAP](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Access_to_MIME_message_parts_and_partial_fetch).

*Store* email *sent*.
Email sent via SMTP.
Store email [via Bcc and filtering fetch](https://en.wikipedia.org/w/index.php?title=Internet_Message_Access_Protocol&oldid=797799352#Disadvantages).

### Won't

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
