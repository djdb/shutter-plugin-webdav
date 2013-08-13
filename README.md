# shutter-plugin-webdav

[Shutter](http://shutter-project.org/) upload plugin based on [WebDAV](http://en.wikipedia.org/wiki/WebDAV). Allows you to push images on WebDAV-enabled server from shutter in two clicks.

## Requirements (shutter side)

perl [HTTP::DAV](http://search.cpan.org/~pcollins/HTTP-DAV-0.31/DAV.pm) module

### via apt (Ubuntu / Debian)

~~~
apt-get install libhttp-dav-perl
~~~

### via perl CPAN

~~~
cpan
cpan> install HTTP::DAV
~~~

## Requirements (server side)

### Ubuntu / Debian

* enabled apache2 dav, dav_fs modules

~~~
a2enmod dav
a2enmod dav_fs
~~~

* Configured WebDAV location. Example:

~~~
<Location /i>
        Order Allow,Deny
        Allow from all
        Dav On
        Options -Indexes

        AuthType Basic
        AuthName DAV
        AuthUserFile /var/www/i/.passwd

        <LimitExcept GET OPTIONS>
                Require user username
        </LimitExcept>
</Location>
~~~

## Installation

* Fetch WebDAV.pm to Shutter's upload_plugins/upload directory
* Adjust variables inside WebDAV.pm file (marked with # edit)

~~~
git clone https://github.com/djdb/shutter-plugin-webdav
sudo cp shutter-plugin-webdav/WebDAV.pm /usr/share/shutter/resources/system/upload_plugins/upload
sudo vim /usr/share/shutter/resources/system/upload_plugins/upload/WebDAV.pm
~~~
