This guide with allow you to complete the following on Ubuntu 12.04

----------------------------------------------------------------------


- Install Deluged 1.3.6
- Install Deluge-web 1.3.6
- Install LibTorrent 0.16.16.0


----------------------------------------------------------------------
Step 1. Install required dependencies for the above applications.


apt-get install python-libtorrent python-libtorrent libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev


----------------------------------------------------------------------
Step 2. Download the LibTorrent-rasterbar files from the following Google Code location.

https://code.google.com/p/libtorrent/

Note: For me this was libtorrent-rasterbar-0.16.16.tar.gz as it was the latest version.


----------------------------------------------------------------------
Step 3. Extract the LibTorrent-rasterbar files.

tar xfv libtorrent-rasterbar-0.16.16.tar.gz


----------------------------------------------------------------------
Step 4. Move into the directory and start the configuration process on the source files.

cd libtorrent-rasterbar-0.16.16/
./configure --enable-python-binding


----------------------------------------------------------------------
Step 5. Make the package, and complete the installation.

make
make install


----------------------------------------------------------------------
Step 6. Build and install the Python files.

cd bindings/python/
python setup.py build
python setup.py install


----------------------------------------------------------------------
Step 7. UpdateDB and locate the libtorrent-rasterbar install location.

updatedb
locate libtorrent-rasterbar.so.*


----------------------------------------------------------------------
Step 8. Update the export location to allow Python to install it.

export LD_LIBRARY_PATH=/<path_to_directory>/ <-- This is found with the above locate command.

For me it was the below.

export LD_LIBRARY_PATH=/usr/local/lib/


----------------------------------------------------------------------
Step 9. Check if libtorrent is installed and available.

python -c "import libtorrent as lt; print lt.version"


----------------------------------------------------------------------
Step 10. Download deluged-1.3.6 (From http://git.deluge-torrent.org/deluge)

wget http://git.deluge-torrent.org/deluge/snapshot/deluge-1.3.6.zip
unzip deluge-1.3.6.zip
cd deluge-1.3.6.zip


----------------------------------------------------------------------
Step 11. Install deluged and deluge-web

python setup.py install


----------------------------------------------------------------------
Step 12. Check its detecting the correct version of LibTorrent

deluge-web --version
deluged --version


----------------------------------------------------------------------

You are now done, try and visit your deluge front end and enable proxy and test the download of the torrent files.

----------------------------------------------------------------------
THIS INFORMATION WAS COLLECTED FROM THE FOLLOWING LOCATIONS ON THE WEB.
----------------------------------------------------------------------
----------------------------------------------------------------------

https://github.com/iMeZz2014/Deluged-1.3.6---deluge-web-with-LibTorrent-0.16.13.0-on-Ubuntu-13
https://code.google.com/p/libtorrent/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Type%20Status%20Priority%20Milestone%20Owner%20Summary&groupby=&sort=&id=439
https://coderwall.com/p/muvnow
http://stackoverflow.com/questions/14047653/python-bindings-for-libtorrent-rasterbar-are-not-working
http://forum.deluge-torrent.org/viewtopic.php?f=7&t=35669
http://forum.deluge-torrent.org/viewtopic.php?f=7&t=45275
http://thrift.apache.org/docs/install/ubuntu/
http://stackoverflow.com/questions/12578499/install-boost-on-ubuntu
http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html
http://forum.deluge-torrent.org/viewtopic.php?f=7&t=45725
