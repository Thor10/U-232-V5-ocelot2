# U-232-V5

```
   _   _   _   _   _     _   _   _   _   _   _     _   _   _   _
  / \ / \ / \ / \ / \   / \ / \ / \ / \ / \ / \   / \ / \ / \ / \
 ( U | - | 2 | 3 | 2 )-( S | O | U | R | C | E )-( C | O | D | E )
  \_/ \_/ \_/ \_/ \_/   \_/ \_/ \_/ \_/ \_/ \_/   \_/ \_/ \_/ \_/

```

##UPDATED 01-Nov-2019

Password hashing switched over to bcrypt.
OMDB/TMDB/YouTube mod has been incorperated. Page added to staff panel for adding API Keys easily.


U-232 V5 -> High performance Bittorrent tracker

## Credits

All Credit goes to the original code creators, and especially to any author for the modifications I selected for U-232.

The original coders of torrentbits and especially to CoLdFuSiOn for carrying on the legacy with Tbdev.

Ocelot is a BitTorrent tracker written in C++ for the Gazelle project and modified for U-232 - <https://github.com/WhatCD/Ocelot>

PimpMyLog - <http://pimpmylog.com/> - <https://github.com/potsky/PimpMyLog>

The coders of gazelle for the `class.cache` and `tracker.class`, *sctbdev* for various replacement code.

All other snippets, mods and contributions for this version from *CoLdFuSiOn*, *putyn, *pdq*, *djGrrr*, *Retro*, *elephant*, *ezero*, *Alex2005*, *system*, *sir_Snugglebunny*, *laffin*, *Wilba*, *Traffic*, *dokty*, *djlee*, *neptune*, *scars*, *Raw*, *soft*, *jaits*, *Melvinmeow*, *RogueSurfer*, *stoner*, *Stillapunk*, *swizzles*, *autotron*, *stonebreath*, *whocares*, *Tundracanine*. 

U-232 wants to thank everyone who helped make it what it is today; shaping and directing our project, all through the thick and thin. It wouldn't have been possible without you. This includes our users and especially Beta Testers - thanks for installing and using u-232 source code as well as providing valuable feedback, bug reports, and opinions.

## The Team

### Lead Coders

- *Mindless*
- *autotron*
- *Stoner*
- *Stonebreath*
- *whocares*

### Support coders & Beta tests

- *ChubbyNinja*
- *BunkerBengt*
- *Tundracanine*
- *son*

### Support Specialists

- Credit's to *pdq*, *putyn* and *elephant* for improvements in key areas on the code. Your input has been first class.

### Lead Designer

- *Swizzles*

### Designers Support

- Credit's to *Kidvision* & others for designs used in the v0+v1+v2 Installer projects.
- Credit's to *Roguesurfer* for all v3 and v4 design - Your a credit to this team.
- Credit's to son for v5 design work.
- Credit's to swizzles and mistero for their work on framework intergration and design layout for v4.

## Special Thanks

### Consulting Developers

Huge thanks to pdq for so much input and improved code and guidance with `memcache`.

Huge thanks to elephant for the XBT edits.

### Beta Testers

The invaluable few who tirelessly find bugs, provide feedback, and drive the developers crazier.

### Language Translators

- *iseeyoucopy*
- *whocares*
- *Tundrcanine*

Thank you for your efforts which make it possible for people all around the world to use U-232.

> THERES TO MANY TO MENTION HERE BUT THE UPMOST RESPECT AND CREDIT TO YOU ALL.

## Support Forum

- <https://forum-u-232.servebeer.com>

## Test site

- <https://u-232.servebeer.com>

## IRC

- `irc.mibbit.com #09source`

## Server set Up Instructions:


U-232 V5 requires the following :

- Memcached
- PHP7.2
- PHP7-CURL
- PHP7-IGBINARY
- PHP7-JSON
- PHP7-MEMCACHED
- PHP7-MSGPACK
- PHP7-MCRYPT
- PHP7-MYSQL/MYSQLI
- PHP7-MBSTRING
- PHP7-GD
- PHP7-GEOIP
- PHP7-OPCACHE
- PHP7-XML
- PHP7-ZIP
- LIBAPACHE2-MOD-PHP7
- Apache/2.4.10
- Mysql 5.5.50-0


### Set Up Instructions:

#### Ocelot

- <https://github.com/WhatCD/Ocelot>
- <https://github.com/whocares-openscene/Ocelot>

Ocelot is a BitTorrent tracker written in C++ for the Gazelle project and modified for U-232. It supports requests over TCP and can only track IPv4 peers.

###### Installing under Linux

- Debian 8

Use the following commands to install the C++ dependencies on Debian. The g++ version should be at least 4.7.


```bash
apt-get install g++ ca-certificates autoconf git make g++ libbz2-dev libtcmalloc-minimal4 libev-dev libmysql++-dev python-dev python3-dev screen
cd ~
wget https://downloads.sourceforge.net/project/boost/boost/1.63.0/boost_1_63_0.tar.gz
tar xfz boost_1_63_0.tar.gz
cd boost_1_63_0
./bootstrap.sh --prefix=/usr/local
./b2 stage toolset=gcc cxxflags=-std=gnu++11 threading=multi link=shared
./b2 install toolset=gcc cxxflags=-std=gnu++11 threading=multi link=shared
cd ~
wget https://ftp.gnu.org/gnu/automake/automake-1.15.tar.gz
tar xfz automake-1.15.tar.gz
cd automake-1.15
./configure && make && make install
ldconfig
```
- Centos/RedHat

Use the following commands to install some of the C++ dependencies on CentOS, Fedora Core and Red Hat. The g++ version should be at least 4.7.

```bash
##Need to update yum install boost-devel gcc-c++ mysql-devel
```

Enter the following commands in a terminal. Be patient while g++ is running, it'll take a few minutes.

- Geting sources other requirements and compiling

```bash
cd ~
git clone https://github.com/whocares-openscene/Ocelot.git
cd Ocelot
./configure --with-mysql-lib=/usr/lib/ --with-ev-lib=/usr/lib/x86_64-linux-gnu/
make
make install
cp ocelot.service /etc/systemd/system/ocelot.service
systemctl enable /etc/systemd/system/ocelot.service
```

> Remember to add your mysql connect details TO /var/www/ocelot.conf

If no errors occurred during install then to start ocelot tracker run

```bash
service ocelot start
```

To stop ocelot

```bash
service ocelot stop
```

#### Upgrade to U-232 V5

If running the upgrade sql then you need to check a few points first:

- Go to your `phpmyadmin` and check what the last id is on `cleanup_manager` and edit the `upgrade.sql` inserts accordingly.
- Check the staff panel last id and edit the upgrade.sql inserts accordinally, `userclasses` in `class_config` table are default 0-6 so if you have different classes then edit that table first adding the new classes and values also edit `cache/class_config.php`.
- Once your upgrade is completed with new code in place simply edit your announce urls in all seeding torrents and change `announce.php?passkey=` to `announce.php?torrent_pass=` and all torrents should resume as normal, same applies if switching to `OCELOT_TRACKER`, you would use the `OCELOT_TRACKER` format for announce url in client.
- Open the `upgrade.sql` and update your database adding all additional entries, once done backup `cache/staff_settings.php` also `cache/staff_settings2.php`, backup `include/ann_config.php and include/config.php`, then delete all the old v4 files from `ftp` except `pic` folder, `torrents`, then upload the v5 code onto your server except the install folder, when prompted at pic folder hit skip and it will only add the newer files depending on ftp client. Open your `ann_config.php` and `config.php` files then open the `install/extra/ann_config.sample.php` and `config.sample.php`, transfer all your config settings to the newer files then save and rename them removing.sample out the file name, then transfer them into include folder, ensure you chmod any new cache files added also.

#### Set up U-232 V5

> **Please take note**:
> Before you begin installation it is very important that your server is configured correctly and has all the required source code dependencies.

Ensure your error reporting is enabled on the server and you are logging the errors and not displaying them.

A error on install is a failure to adhere to setup instructions.

If you experience a failure then a properly configured server will report that issue, no excuses required.

Install `memcached` and zend `opcode` cache before installing U-232 V5.

1. Create a directory one up from root so it resides beside it not inside it, named bucket.
	1. Then inside the bucket folder make another and name it avatar, remember to chmod them to 777
	2. If you use your own names for those folders then you need to edit `bitbucket.php` and `img.php` defines at top of the files.
	3. Then add a `.htaccess` and `index.html` files into both newly created folders.
	4. Then chmod those above folders.
	5. Then extract `pic.tar.gz`, `Log_Viewer.tar.gz` and `GeoIp.tar.gz` and ensure they are not inside an extra folder from being archived.
	6. Then upload the code to your server and `chmod`: 
		- `cache` and all nested files and folders.
		- `dir_list`
		- `uploads`
		- `uploadsub`
		- `imdb/cache`
		- `imdb/images`
		- `include`
		- `include/backup`
		- `include/settings/settings.txt`
		- `install/extra/config.phpsample.php/config.ocelotsample.php`
		- `install/extra/ann_config.phpsample.php/ann_config.ocelotsample.php`
		- `sqlerr_logs`
		- `torrents`

2. Create a new database user and password via `phpmyadmin`.

3. Point to <https://yoursite.com/install/index.php> - *fill in all the required data and choose ocelot or default* - then log in.

4. Create a second user on entry named System ensure it's user id = 2 so you don't need to alter the `autoshout` function on `include/user_functions.php`.

5. `Sysop` is added automatically to the array in `cache/staff_settings.php` and `cache/staff_setting2.php`.

6. `Staff` is automatically added to the same two files, but you have to make sure the member is offline before you promote them.

Side note on Mysql 5.7: Mysql 5.7 And MariaDB 10.2 will not work with U-232, We recommend you use Mysql 5.5 or MariaDB 10.1 @ https://downloads.mariadb.org/mariadb/10.1.26/
