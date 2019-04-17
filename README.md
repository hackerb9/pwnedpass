# pwnedpass
Securely check if a password is known in Troy Hunt's Pwned Passwords database

![Example of pwnedpass usage](/README.md.d/example1.png "./pwnedpass passwordhere")

## Install and usage

Just download the `pwnedpass` script, chmod it, and run it.

    wget https://github.com/hackerb9/pwnedpass/raw/master/pwnedpass
    chmod +x pwnedpass
    ./pwnedpass MyPassword1
    
Don't want your password saved in your .history file? No problem. Just run `./pwnedpass` without any arguments and it'll prompt your for the password to check. 

## What is pwnedpass?

Pwnedpass reads in a password and prints out whether it has been seen
in previous security breaches using Troy Hunt's "pwned password"
database.

This script is for people who don't want to plug their password into
[random third party websites](https://haveibeenpwned.com/Passwords) to
see if it is a known password. While I trust Troy Hunt, I don't trust
that his web service won't get hijacked and dynamically load malicious
Javascript. This shell script solves that problem by being short
enough that anyone can verify that it is secure before they run it on
their own machine.

Actual passwords are _never_ sent on the Internet. Instead, a SHA1
hash is taken and only the first five characters of the hash are sent.
The database returns around 500 possible hashes that begin with that
prefix and we grep to see if ours is among them.

You can read more about Troy Hunt's database here:
https://www.troyhunt.com/ive-just-launched-pwned-passwords-version-2/

## Memorizable passwords that are secure

Troy Hunt is big on keeping all your passwords in a program which is
unlocked by a master password. I'm not a fan of that as I see it as
putting too many eggs in one basket (and then painting a bullseye on
the basket for ne'er-do-wells to aim for) .

I prefer a tiered approach: strong passwords and [FIDO2 hardware
keys](https://solokeys.com) for banks, shopping, and e-mail. A medium password
for various social media accounts. A weak password for the zillions of
sites that insist I give them a password, although I actively distrust
them.

If you want to create a memorable password, try using hackerb9's
[`mkpass`](https://github.com/hackerb9/mkpass/) program which uses an
[XKCD 936](https://xkcd.com/936/) compliant generation method, but
allows you to use a corpus of documents with words salient to you
rather than a generic dictionary. (The _bag_ _fifty_ _rose_ _standing_
example above is a password created using Andrew Lang's Fairy Books as
the source of words.) 
