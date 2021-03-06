# vim-mail: send mails from within Vim

A Vim wrapper around a Python3 script (uses `smtplib`) to send emails from
Vim. Most Vim stuff is based on
[vim-scripts/MailApp](https://github.com/vim-scripts/MailApp). The Python
script is made by myself.

## Requirements
- configparser (`pip3 install configparser`)
- an iCloud/gmail email address with an app specific password
  ([iCloud](imore.com/how-generate-app-specific-passwords-iphone-ipad-mac),
  [gmail](https://www.lifewire.com/get-a-password-to-access-gmail-by-pop-imap-2-1171882))
- The email address and password in KeyChain

## Get Started
1. Add a new entry to the Keychain: go to the `Keychain Acces` app, click on
   the `+` button on the left. Fill in:
   - `Keychain Item Name`: the server (`appleid.apple.com` for icloud)
   - `Account Name`: your username
   - `Password`: your app specific password
2. Create a config file at `~/.config/mailer/config` with the following
   content:

   ```ini
   [you@yourmail.com]
   username = you@yourlogin.com
   server = appleid.apple.com
   smtp_server = smtp.mail.me.com # apple's smtp server
   ```
   Multiple sections are possible for handling multiple accounts.
3. Open Vim and set the filetype to mailapp (`:set ft=mailapp`), press TAB to
   get 1) FROM: 2) TO: 3) SUBJECT:. Fill in and start typing your mail.
4. When done typing the mail, type `:SendMail`.

## Command Line Usage
```
mailer [--from YOUR_OTHER_MAIL] --to RECIEVING_MAIL --subject SUBJECT --body CONTENT
```
Example:
```
mailer --to someone@gmail.com --subject Just wanna say hi --body hi.
```

## Extra!
Use this alias for creating a new mail quick:
```bash
alias newmail='$VISUAL /tmp/vim-mail-$(date +%s).mail'
```
You can close the file and edit it later on. It's awesome.

## Licence
MIT.
