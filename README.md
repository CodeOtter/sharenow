# sharenow
Securely share small files in CLI.

## Installation

```
apt-get update
apt-get install curl openssl python
sudo curl -o /usr/local/bin/sharenow https://raw.githubusercontent.com/CodeOtter/sharenow/master/sharenow && sudo chmod 755 /usr/local/bin/sharenow
```

## Usage

To share a file or folder:

``sharenow <filename>``

The file/directory will be archived, then encrypted via OpenSSL.  You will be asked to enter a password for the encryption.  The encrypted output will be in Base64 and posted to HasteBin.  The token for that location will be outputted to your terminal.  Copy and paste it to the recipients.  

The recipients then type:

``sharenow -d <token>``

This will fetch the HasteBin contents and ask you for a password to decrypt them.   It's best for you and your recipients to agree to a password ahead of time so your recipients do not ask you for the password over the internet.  Once decrypted, the contents will be decompressed and unarchived at your current working directory.

## One-Time Pad: Maximium Security

For maximum security, confer with your recipients ahead of time (preferably offline and away from mobile phones) to agree to possess a copy of a shared book.  You then generate passwords from this book at random, keeping track of where the password can be found in the book.  For example, if you select a passage "*Idaho shook his head*" from the May 1983 second printing of **God Emperor of Dune**, that passage can be found on page 336, starting with the 16th word and ending with the 19th word.  When you give the token to your recipients, you would do so as this:

``gathlmpotn 336 16 19``

Or

``gathlmpotn 336 16 3``

This way, the password is never sent over the internet.  Sharenow uses the ``-salt`` flag with OpenSSL reduce your expose to dictionary attacks.