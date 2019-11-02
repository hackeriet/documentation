# How to add keys to the Humla doorbot

## Adding a keycard

1.  Log in to humladoor: `ssh pi@humladoor`
2.  look at logfile for door: `tail -f /var/log/door.log`
3.  swipe the card you wish to add
4.  copy the full card number from the console output into
    `/home/pi/users/$username`

The first numbers should match the numbers printed on the card. The last
number doesn't match the one on the card. The leading zeroes should not be included!

## Adding an ssh key

You can use ssh to open the door, for instance from your cell phone or
laptop.
This happens automatically if you put your ssh key into the lock.

It's also a practical way of letting someone in remotely.

1.  Log in to humladoor: `ssh pi@humladoor`
2.  Get root: `sudo -i`
3.  Switch directories: `cd ~humla`
4.  Paste your ssh key at the end of the authorized keys file `vim .ssh/authorized\_keys`

Now you can open the lock with

```
ssh humla@humladoor
```
