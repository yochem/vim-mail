# vim-mail: send mails from within Vim

A Vim wrapper around a Python3 script (uses `smtplib`) to send emails from
Vim. Most Vim stuff is based on
[vim-scripts/MailApp](https://github.com/vim-scripts/MailApp). The Python
script is made by myself.

:warning: Currently only works with iCloud mail on MacOS. This is because it
uses MacOS' Keychain to get the password of the mail account.

## Requirements
- configparser (`pip3 install configparser`)
- an iCloud email address with an app specific password ([How to generate app
    specific password](imore.com/how-generate-app-specific-passwords-iphone-ipad-mac))
- The email address and password in KeyChain

## Get Started
1. Place `mailer` in `$PATH`
([how](https://stackoverflow.com/questions/20054538/add-a-bash-script-to-path))
2. Add a new entry to the Keychain:
   ```
   > keychain acces
   > +
   > Keychain item name: https://appleid.apple.com,
     Account name: your@appleid.com
     Password: YOUR_APP_SPECIFIC_PASSWORD
   > Add
   ```
3. Create a config file at `~/.config/mailer/mailerrc` with the following
   content:
   ```ini
   [you@icloud.com]
   apple_id = your@appleid.com
   ```
   Multiple sections are possible for handling multiple accounts.

## Command Line Usage
```
mailer [--from YOUR_OTHER_MAIL] --to RECIEVING_MAIL --subject SUBJECT --body CONTENT
```
Example:
```
mailer --to someone@gmail.com --subject Just wanna say hi --body hi.
```

## Licence
MIT.
