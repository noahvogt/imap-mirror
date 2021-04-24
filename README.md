# Imap Mirror

This program allows you to forward unread emails, mark them as read and send them to the another email server.

Note this is done **only with imap servers**. So it doesn't actually forward the email, it just appends unread emails from the sending imap server to the receiving imap server. This is a lot cleaner:

- you don't have to worry about reformatting email headers
- on responding, the receiver won't see that your email was forwarded
- on responding, there is no trace anymore of the email address that originally received the email (it looks like it the email was instead sent to the mirrored email server)

## Dependencies

You only need *python3* for the actual program - as all libraries used come with a default python installation - and a POSIX-compatible shell for the wrapper script.

## Usage

### Setup Config

Copy the ```default.config.ini``` template to ```config.ini``` and edit it accordingly. The *'user'* entry usually refers just to the email adress. When you don't know what port is needed, just put ```993``` in *'port'* as this is the standard port for imap servers.

### Use the wrapper script

On your server box / VPS, run the ```wrapper &``` POSIX shell script, so you don't ever have to worry about running this manually on your local machines.

The default sleep time between the rerunning is 60 seconds, but you can change this with running ```wrapper [seconds] &```.

## Security

Your email credentials are saved in plain text inside of ```config.ini```, so make sure to **never** publish or commit it using git publicly. This is also why I added this file to *.gitignore*.

I because of this and practical reasons, I would recommend to just run this program on your properly secured server box or VPS.

## Future Features

- accept multiple sending addresses
