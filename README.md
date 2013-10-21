Synthesize
==========

Installing Graphite doesn't have to be difficult. The `install` script in synthesize is designed to make it brain-dead easy to install Graphite and related services onto a modern Linux distribution.

Synthesize is built to run on Ubuntu 13.10. It will __not__ run on other Ubuntu releases or Linux distributions. The goal of this project is not to become an automation alternative to modern configuration management utilities (e.g. Chef or Puppet), but rather, to make it as easy as possible for the beginner Graphite user to get started and familiar with the project without having to learn a suite of other automation and/or infrastructure-related projects.

The resulting Graphite server __listens only on https port 443__ and has been configured to collect metrics specifically for helping profile the performance of your Graphite and Carbon services. It uses memcached for improved query performance, and Statsite for a fast, C-based implementation of the StatsD collector/aggregator.

## Provides

* Graphite 0.9.12 ([graphite-web](https://github.com/graphite-project/graphite-web), [carbon](https://github.com/graphite-project/carbon), [whisper](https://github.com/graphite-project/whisper))
* StatsD ([statsite](https://github.com/armon/statsite))
* collectd agent

## Dependencies

* An Ubuntu 13.10 VM or server
* Some mechanism for downloading Synthesize

## Installation

```
$ cd synthesize
$ ./install
```

## Removal

```
$ cd synthesize
$ ./uninstall
```

## License

Synthesize is distributed under the MIT license.

