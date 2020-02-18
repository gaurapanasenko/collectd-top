# CollectD plugin for top processes statistics

`collectd-top` is a `collectd-python` plugin for pushing statistics from
the `ps` utility to collectd.

## Installation

Requires `collectd-python` package. On Centos 7,

```shell
$ yum install collectd-python
```

While this is somewhat environment specific, based on the configuration
in `10-top.conf`, the module files should be located inside `/usr/lib/collectd`,

```shell
$ cp collectd_top.py /usr/lib/collectd/
```

The configuration file (10-top.conf) should be either placed in a path that is
included within collectd.conf, for e.g. if it there is a line in collectd.conf
such as -
```
Include "/etc/collectd/managed_config/*.conf"
```
then 10-top.conf should be placed in the managed_config folder.

Use puppet to create module files or manually create one,

```shell
$ nano 10-top.conf
```

```
LoadPlugin python

<Plugin python>
    ModulePath "/usr/lib/collectd.d"
    Import "cuda_collectd"
</Plugin>
```
