Synthesize
==========

[![Install on DigitalOcean](http://installer.71m.us/button.svg)](http://installer.71m.us/install?url=https://github.com/obfuscurity/syntesize)

Installing Graphite doesn't have to be difficult. The `install` script in synthesize is designed to make it brain-dead easy to install Graphite and related services onto a modern Linux distribution.

Synthesize is built to run on Ubuntu 14.04 LTS. It will __not__ run on other Ubuntu releases or Linux distributions. The goal of this project is not to become an automation alternative to modern configuration management utilities (e.g. Chef or Puppet), but rather, to make it as easy as possible for the beginner Graphite user to get started and familiar with the project without having to learn a suite of other automation and/or infrastructure-related projects.

The resulting Graphite server __listens only on https port 443__ and has been configured to collect metrics specifically for helping profile the performance of your Graphite and Carbon services. It uses memcached for improved query performance, and Statsite for a fast, C-based implementation of the StatsD collector/aggregator.

**WARNING:** You should not install Synthesize directly on your personal development system. It's strongly suggested that you use a VM or other temporary VPS instance for sandboxing Synthesize.

## Provides

* Graphite 0.9.12 ([graphite-web](https://github.com/graphite-project/graphite-web), [carbon](https://github.com/graphite-project/carbon), [whisper](https://github.com/graphite-project/whisper))
* StatsD ([statsite](https://github.com/armon/statsite))
* collectd agent

## Dependencies

* Vagrant, an Ubuntu 14.04 VM or a non-production server
* Some mechanism for downloading Synthesize

## Installation

### Manual

```
$ cd synthesize
$ sudo ./install
```

### Vagrant

Synthesize configures the following host ports to forward to the private vagrant box:

```
config.vm.network :forwarded_port, guest: 443, host: 8443
config.vm.network :forwarded_port, guest: 8125, host: 8125
config.vm.network :forwarded_port, guest: 2003, host: 22003
config.vm.network :forwarded_port, guest: 2004, host: 22004
```

```
$ cd synthesize
$ vagrant plugin install vagrant-vbguest
$ vagrant up
```

## Administration

There is a superuser (Django) account that grants access to the administrative features in the backend Django database. The default credentials are:

* username `admin`
* password `graphite_me_synthesize`

These credentials can be changed with the following commands:

```
$ cd /opt/graphite/webapp/graphite
$ sudo python manage.py changepassword admin
```

## Removal

### Manual

```
$ cd synthesize
$ ./uninstall
```

### Vagrant

```
$ cd synthesize
$ vagrant destroy
```

## License

Synthesize is distributed under the MIT license.

