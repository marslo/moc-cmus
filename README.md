Moc-Cmus_Config
===============

The configuration about MOCP

##Usage
- Copy the .moc folder to $HOME
    <pre><code>$ cp -r .moc ~/
    </code></pre>
- If show error: `Configuration file is not secure: /home/marslo/.moc/config`, then set the file mode of config as 755:
    <pre><code>$ chmod 755 ~/.moc/config
    </code></pre>

## Build moc by souce code
### Precondiction:
- Download source code from [Official Web Site](http://moc.daper.net/download)
- [moc-2.5.0-beta1](http://ftp.daper.net/pub/soft/moc/unstable/moc-2.5.0-beta1.tar.bz2)
- [DEB packages FTP](http://ftp.de.debian.org/pub/debian/pool/main/m/moc/)

### Errors and Soluctions
- **error: BerkeleyDB (libdb) not found**
<pre><code>sudo apt-get install libdb++-dev libdb-dev
</code></pre>
- **decoder.c:22:18: fatal error: ltdl.h**
<pre><code>sudo apt-get install libltdl-dev
</code></pre>
- **FATAL_ERROR: No valid sound driver!**
    - Error:
        <pre><code>[marslo@MarsloJiao ~]
        $ mocp
        Running the server...
        Trying OSS...
        FATAL_ERROR: No valid sound driver!
        FATAL_ERROR: Server exited!
        [marslo@MarsloJiao ~]
        $ gdb mocp core
        GNU gdb (GDB) 7.6.1-ubuntu
        Copyright (C) 2013 Free Software Foundation, Inc.
        License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
        This is free software: you are free to change and redistribute it.
        There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
        and "show warranty" for details.
        This GDB was configured as "i686-linux-gnu".
        For bug reporting instructions, please see:
        <http://www.gnu.org/software/gdb/bugs/>...
        Reading symbols from /home/marslo/Tools/Software/SourceCode/Moc/moc-2.5.0-beta1/mocp...done.
        /home/marslo/Tools/Software/SourceCode/Moc/moc-2.5.0-beta1/core: No such file or directory.
        (gdb) run
        Starting program: /home/marslo/Tools/Software/SourceCode/Moc/moc-2.5.0-beta1/mocp
        [Thread debugging using libthread_db enabled]
        Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
        Running the server...
        Trying OSS...
        FATAL_ERROR: No valid sound driver!
        FATAL_ERROR: Server exited!
        [Inferior 1 (process 18165) exited with code 02]
        (gdb) exit
        Undefined command: "exit".  Try "help".
        (gdb) quit
        </code></pre>

    - Soluction
        <pre><code>
        sudo apt-get install libncurses5-dev libncursesw5-dev libasound2-dev libvorbis-dev libmad0-dev libid3tag0-dev zlib1g-dev libsndfile1-dev libflac-dev libogg-dev libsamplerate0-dev libspeex-dev libmpcdec-dev libsidplay2-dev libsidutils-dev libresid-builder-dev libwavpack-dev libtagc0-dev libcurl4-gnutls-dev libavcodec-dev libavformat-dev libltdl3-dev libtool libmodplug-dev automake1.9 autoconf
        </code></pre>

        <pre><code> [marslo@MarsloJiao ~]
        $ sudo apt-get install libncurses5-dev libncursesw5-dev libasound2-dev libvorbis-dev libmad0-dev libid3tag0-dev zlib1g-dev libsndfile1-dev libflac-dev libogg-dev libsamplerate0-dev libspeex-dev libmpcdec-dev libsidplay2-dev libsidutils-dev libresid-builder-dev libwavpack-dev libtagc0-dev libcurl4-gnutls-dev libavcodec-dev libavformat-dev libltdl3-dev libtool libmodplug-dev automake1.9 autoconf
        Reading package lists... Done
        Building dependency tree
        Reading state information... Done
        Note, selecting 'libltdl-dev' instead of 'libltdl3-dev'
        libltdl-dev is already the newest version.
        libncurses5-dev is already the newest version.
        libncursesw5-dev is already the newest version.
        libogg-dev is already the newest version.
        libogg-dev set to manually installed.
        libtool is already the newest version.
        libtool set to manually installed.
        libvorbis-dev is already the newest version.
        zlib1g-dev is already the newest version.
        libavcodec-dev is already the newest version.
        libavcodec-dev set to manually installed.
        libavformat-dev is already the newest version.
        The following packages were automatically installed and are no longer required:
          librcc0 librcd0 linux-headers-generic linux-image-generic
        Use 'apt-get autoremove' to remove them.
        The following extra packages will be installed:
          comerr-dev krb5-multidev libgssrpc4 libidn11-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-6
          libkrb5-dev libldap2-dev librtmp-dev libsigsegv2 libtag1-dev m4
        Suggested packages:
          autoconf2.13 autoconf-archive gnu-standards autoconf-doc automake1.9-doc krb5-doc libasound2-doc
          libcurl4-doc libcurl3-dbg krb5-user
        Recommended packages:
          automake automaken
        The following NEW packages will be installed:
          autoconf automake1.9 comerr-dev krb5-multidev libasound2-dev libcurl4-gnutls-dev libflac-dev libgssrpc4
          libid3tag0-dev libidn11-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-6 libkrb5-dev libldap2-dev
          libmad0-dev libmodplug-dev libmpcdec-dev libresid-builder-dev librtmp-dev libsamplerate0-dev
          libsidplay2-dev libsidutils-dev libsigsegv2 libsndfile1-dev libspeex-dev libtag1-dev libtagc0-dev
          libwavpack-dev m4
        0 upgraded, 30 newly installed, 0 to remove and 16 not upgraded.
        Need to get 6,250 kB of archives.
        After this operation, 16.9 MB of additional disk space will be used.
        ....
        </code></pre>
        - Check alas-base and alas-utils
        <pre><code>[marslo@MarsloJiao ~]
        $ dpkg -l alsa-base
        Desired=Unknown/Install/Remove/Purge/Hold
        | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
        |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
        ||/ Name                 Version         Architecture    Description
        +++-====================-===============-===============-==============================================
        ii  alsa-base            1.0.25+dfsg-0ub all             ALSA driver configuration files
        [marslo@MarsloJiao ~]
        $ dpkg -l alsa-utils
        Desired=Unknown/Install/Remove/Purge/Hold
        | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
        |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
        ||/ Name                 Version         Architecture    Description
        +++-====================-===============-===============-==============================================
        ii  alsa-utils           1.0.27.1-1ubunt i386            Utilities for configuring and using ALSA
        </code></pre>

##Screenshot
### Moc (Music on console)
![My_Mocp](https://github.com/Marslo/Moc-Cmus_Config/blob/master/screenshots/MOCP_Screenshot.png?raw=true)

### Cmus
![My_Cmus](https://github.com/Marslo/Moc-Cmus_Config/blob/master/screenshots/cmus2.png?raw=true)
