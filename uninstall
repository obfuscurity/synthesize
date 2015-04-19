#!/bin/bash
# Graphite uninstall script for Ubuntu 13.10 x64
# Jason Dixon <jason@dixongroup.net>

service carbon-cache stop
service memcached stop
service collectd stop
service apache2 stop
service statsite stop

# Remove various binaries, configuration files, and source directories
rm /usr/local/sbin/statsite*
rm /etc/statsite.conf
pip uninstall -y -r /usr/local/src/graphite-web/requirements.txt
pip uninstall -y -r /usr/local/src/carbon/requirements.txt
pip uninstall --egg SCons
rm -r /opt/graphite
rm -r /usr/local/src/graphite-web
rm -r /usr/local/src/carbon
rm -r /usr/local/src/whisper
rm -r /usr/local/src/statsite
rm /usr/local/bin/*whisper*.py
rm /usr/local/lib/python2.7/dist-packages/whisper*
rm /etc/apache2/sites-*/graphite.conf
rm /etc/init/graphite.conf
rm /etc/init/statsite.conf
rm /etc/cron.hourly/graphite-build-index

# Uninstall our package dependencies and purge configurations
apt-get purge -y python-cairo python-django python-django-tagging python-twisted python-zope.interface fontconfig apache2 libapache2-mod-wsgi python-pysqlite2 python-simplejson python-memcache git-core collectd memcached gcc g++ make
apt-get autoremove -y

# Brute force cleanup on the collectd configuration directory
rm -r /etc/collectd

# Remove our system user for Carbon
pkill -9 -f carbon-cache
userdel carbon
