CouchPotato
=====

[![Join the chat at https://gitter.im/RuudBurger/CouchPotatoServer](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/RuudBurger/CouchPotatoServer?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

CouchPotato (CP) is an automatic NZB and torrent downloader. You can keep a "movies I want"-list and it will search for NZBs/torrents of these movies every X hours.
Once a movie is found, it will send it to SABnzbd or download the torrent to a specified directory.


## Running from Source

CouchPotatoServer can be run from source. This will use *git* as updater, so make sure that is installed.

Windows, see [the CP forum](http://couchpota.to/forum/showthread.php?tid=14) for more details:

* Install [Python 2.7](http://www.python.org/download/releases/2.7.3/)
* Then install [PyWin32 2.7](http://sourceforge.net/projects/pywin32/files/pywin32/Build%20217/) and [GIT](http://git-scm.com/)
* If you come and ask on the forums 'why directory selection no work?', I will kill a kitten, also this is because you need PyWin32
* Open up `Git Bash` (or CMD) and go to the folder you want to install CP. Something like Program Files.
* Run `git clone https://github.com/RuudBurger/CouchPotatoServer.git`.
* You can now start CP via `CouchPotatoServer\CouchPotato.py` to start
* Your browser should open up, but if it doesn't go to `http://localhost:5050/`

OS X:

* If you're on Leopard (10.5) install Python 2.6+: [Python 2.6.5](http://www.python.org/download/releases/2.6.5/)
* Install [GIT](http://git-scm.com/)
* Open up `Terminal`
* Go to your App folder `cd /Applications`
* Run `git clone https://github.com/RuudBurger/CouchPotatoServer.git`
* Then do `python CouchPotatoServer/CouchPotato.py`
* Your browser should open up, but if it doesn't go to `http://localhost:5050/`

Linux:

* (Ubuntu / Debian) Install [GIT](http://git-scm.com/) with `apt-get install git-core`
* (Fedora / CentOS) Install [GIT](http://git-scm.com/) with `yum install git`
* 'cd' to the folder of your choosing.
* Run `git clone https://github.com/RuudBurger/CouchPotatoServer.git`
* Then do `python CouchPotatoServer/CouchPotato.py` to start
* (Ubuntu / Debian) To run on boot copy the init script `sudo cp CouchPotatoServer/init/ubuntu /etc/init.d/couchpotato`
* (Ubuntu / Debian) Copy the default paths file `sudo cp CouchPotatoServer/init/ubuntu.default /etc/default/couchpotato`
* (Ubuntu / Debian) Change the paths inside the default file `sudo nano /etc/default/couchpotato`
* (Ubuntu / Debian) Make it executable `sudo chmod +x /etc/init.d/couchpotato`
* (Ubuntu / Debian) Add it to defaults `sudo update-rc.d couchpotato defaults`
* (systemd) To run on boot copy the systemd config `sudo cp CouchPotatoServer/init/couchpotato.fedora.service /etc/systemd/system/couchpotato.service`
* (systemd) Update the systemd config file with your user and path to CouchPotato.py 
* (systemd) Enable it at boot with `sudo systemctl enable couchpotato`
* Open your browser and go to `http://localhost:5050/`

Docker:
* You can use [razorgirl's Dockerfile](https://github.com/razorgirl/docker-couchpotato) to quickly build your own isolated app container. It's based on the Linux instructions above. For more info about Docker check out the [official website](https://www.docker.com).

FreeBSD:

* Become root with `su`
* Update your repo catalog `pkg update`
* Install required tools `pkg install python py27-sqlite3 fpc-libcurl docbook-xml git-lite`
* For default install location and running as root `cd /usr/local`
* If running as root, expects python here `ln -s /usr/local/bin/python /usr/bin/python`
* Run `git clone https://github.com/RuudBurger/CouchPotatoServer.git`
* Copy the startup script `cp CouchPotatoServer/init/freebsd /usr/local/etc/rc.d/couchpotato`
* Make startup script executable `chmod 555 /usr/local/etc/rc.d/couchpotato`
* Add startup to boot `echo 'couchpotato_enable="YES"' >> /etc/rc.conf`
* Read the options at the top of `more /usr/local/etc/rc.d/couchpotato`
* If not default install, specify options with startup flags in `ee /etc/rc.conf`
* Finally, `service couchpotato start`
* Open your browser and go to: `http://server:5050/`
