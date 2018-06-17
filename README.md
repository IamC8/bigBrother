# bigBrother

Two scripts to setup and run a seedbox.
It makes use of deluge and privateinternetaccess at this time...

## Getting Started

Get the code.
Install it on a new raspberry pi or debian virtualbox or machine.
make the scripts executable and run 'theBoss'
When it finishes youll have a up and running deluge client, connecting through the vpn with port forwarding set up.

### Prerequisites

An account with
* [PIA Account] (https://www.privateinternetaccess.com) - Your vpn provider
* [Pushbullet] (https://www.pushbullet.com/#settings/account) - Sending notifications to your phone, optional but recommended

A newly installed version of one of the following
* [raspberrypi] (https://www.raspberrypi.org/downloads/raspbian/) - Not Tested. Network restart might need change.
* [Ubuntu 18.04 LTS Minimal] (https://help.ubuntu.com/community/Installation/MinimalCD) - Tested as standalone and on virtualbox.

### Installing
When you have the seedbox up and runnig, ssh into it and download the scripts.
Extract  the files with tar.
  chmod +x theBoss
  populate the config file with your own info
  sudo ./theBoss
  
Follow the instructions and ssh into the box again when a reboot occurred.
Re-run the script again.
And repeat

```
until finished
```
## Checking if al went well
Whilst logged in via ssh type the following:
  sudo su --shell /bin/bash --login vpn_user
Then type:
  ssh -fNL 58888:localhost:58846 USER@$OSTNAME
Accept the fingerprint and enter password.
When all is good, press CTRL D twice to get out of box.
Then from you own machine type:
(Replace the last 'test' with your own i.e. john@10.0.0.5)
  ssh -L 127.0.0.2:58846:localhost:58888 test
Enter your password to ssh to the new box.
Leave the session open and start the deluge client on your own machine.
  Now add a new connection:
  Hostname: 127.0.0.2
  Username: alice
  Password: MyC0mpL3xPass
Read here to change deluge's password: 
[Deluge ThinClient] (https://dev.deluge-torrent.org/wiki/UserGuide/ThinClient)

