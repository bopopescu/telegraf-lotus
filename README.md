# Telegraf (with custom plugins)

Telegraf is an agent for collecting, processing, aggregating, and writing metrics.

Design goals are to have a minimal memory footprint with a plugin system so
that developers in the community can easily add support for collecting
metrics.

For more information about Telegraf, [please visit their repo](https://github.com/influxdata/telegraf/).

## Custom Plugins

This fork includes some plugins which are not intended to be merged upstream (at this time). The
following plugins are unique to this repository.

### Input Plugins

* [lotus](./plugins/inputs/lotus)

## Output Plugins

* [postgresql](./plugins/outputs/postgresql)

## Minimum Requirements

Telegraf shares the same [minimum requirements][] as Go:
- Linux kernel version 2.6.23 or later
- Windows 7 or later
- FreeBSD 11.2 or later
- MacOS 10.11 El Capitan or later

[minimum requirements]: https://github.com/golang/go/wiki/MinimumRequirements#minimum-requirements

## Installation:

### From Source:

Telegraf requires Go version 1.12 or newer, the Makefile requires GNU make.

1. [Install Go](https://golang.org/doc/install) >=1.12 (1.13 recommended)
2. Clone the Telegraf repository: `git clone https://github.com/filecoin-shipyard/telegraf.git`
3. Run `make` from the source directory

## How to use it:

See usage with:

```
telegraf --help
```

#### Generate a telegraf config file:

```
telegraf config > telegraf.conf
```

#### Generate config with only cpu input & influxdb output plugins defined:

```
telegraf --section-filter agent:inputs:outputs --input-filter cpu --output-filter influxdb config
```

#### Run a single telegraf collection, outputing metrics to stdout:

```
telegraf --config telegraf.conf --test
```

#### Run telegraf with all plugins defined in config file:

```
telegraf --config telegraf.conf
```

#### Run telegraf, enabling the cpu & memory input, and influxdb output plugins:

```
telegraf --config telegraf.conf --input-filter cpu:mem --output-filter influxdb
```

## Documentation

[Latest Release Documentation][release docs].

For documentation on the latest development code see the [documentation index][devel docs].

[release docs]: https://docs.influxdata.com/telegraf
[devel docs]: docs

## Input Plugins

* [activemq](./plugins/inputs/activemq)
* [aerospike](./plugins/inputs/aerospike)
* [amqp_consumer](./plugins/inputs/amqp_consumer) (rabbitmq)
* [apache](./plugins/inputs/apache)
* [apcupsd](./plugins/inputs/apcupsd)
* [aurora](./plugins/inputs/aurora)
* [aws cloudwatch](./plugins/inputs/cloudwatch) (Amazon Cloudwatch)
* [azure_storage_queue](./plugins/inputs/azure_storage_queue)
* [bcache](./plugins/inputs/bcache)
* [beanstalkd](./plugins/inputs/beanstalkd)
* [bind](./plugins/inputs/bind)
* [bond](./plugins/inputs/bond)
* [burrow](./plugins/inputs/burrow)
* [cassandra](./plugins/inputs/cassandra) (deprecated, use [jolokia2](./plugins/inputs/jolokia2))
* [ceph](./plugins/inputs/ceph)
* [cgroup](./plugins/inputs/cgroup)
* [chrony](./plugins/inputs/chrony)
* [cisco_telemetry_gnmi](./plugins/inputs/cisco_telemetry_gnmi)
* [cisco_telemetry_mdt](./plugins/inputs/cisco_telemetry_mdt)
* [clickhouse](./plugins/inputs/clickhouse)
* [cloud_pubsub](./plugins/inputs/cloud_pubsub) Google Cloud Pub/Sub
* [cloud_pubsub_push](./plugins/inputs/cloud_pubsub_push) Google Cloud Pub/Sub push endpoint
* [conntrack](./plugins/inputs/conntrack)
* [consul](./plugins/inputs/consul)
* [couchbase](./plugins/inputs/couchbase)
* [couchdb](./plugins/inputs/couchdb)
* [cpu](./plugins/inputs/cpu)
* [DC/OS](./plugins/inputs/dcos)
* [diskio](./plugins/inputs/diskio)
* [disk](./plugins/inputs/disk)
* [disque](./plugins/inputs/disque)
* [dmcache](./plugins/inputs/dmcache)
* [dns query time](./plugins/inputs/dns_query)
* [docker](./plugins/inputs/docker)
* [docker_log](./plugins/inputs/docker_log)
* [dovecot](./plugins/inputs/dovecot)
* [aws ecs](./plugins/inputs/ecs) (Amazon Elastic Container Service, Fargate)
* [elasticsearch](./plugins/inputs/elasticsearch)
* [ethtool](./plugins/inputs/ethtool)
* [eventhub_consumer](./plugins/inputs/eventhub_consumer) (Azure Event Hubs \& Azure IoT Hub)
* [exec](./plugins/inputs/exec) (generic executable plugin, support JSON, influx, graphite and nagios)
* [execd](./plugins/inputs/execd)
* [fail2ban](./plugins/inputs/fail2ban)
* [fibaro](./plugins/inputs/fibaro)
* [file](./plugins/inputs/file)
* [filestat](./plugins/inputs/filestat)
* [filecount](./plugins/inputs/filecount)
* [fireboard](/plugins/inputs/fireboard)
* [fluentd](./plugins/inputs/fluentd)
* [github](./plugins/inputs/github)
* [graylog](./plugins/inputs/graylog)
* [haproxy](./plugins/inputs/haproxy)
* [hddtemp](./plugins/inputs/hddtemp)
* [httpjson](./plugins/inputs/httpjson) (generic JSON-emitting http service plugin)
* [http_listener](./plugins/inputs/influxdb_listener) (deprecated, renamed to [influxdb_listener](/plugins/inputs/influxdb_listener))
* [http_listener_v2](./plugins/inputs/http_listener_v2)
* [http](./plugins/inputs/http) (generic HTTP plugin, supports using input data formats)
* [http_response](./plugins/inputs/http_response)
* [icinga2](./plugins/inputs/icinga2)
* [infiniband](./plugins/inputs/infiniband)
* [influxdb](./plugins/inputs/influxdb)
* [influxdb_listener](./plugins/inputs/influxdb_listener)
* [internal](./plugins/inputs/internal)
* [interrupts](./plugins/inputs/interrupts)
* [ipmi_sensor](./plugins/inputs/ipmi_sensor)
* [ipset](./plugins/inputs/ipset)
* [iptables](./plugins/inputs/iptables)
* [ipvs](./plugins/inputs/ipvs)
* [jenkins](./plugins/inputs/jenkins)
* [jolokia2](./plugins/inputs/jolokia2) (java, cassandra, kafka)
* [jolokia](./plugins/inputs/jolokia) (deprecated, use [jolokia2](./plugins/inputs/jolokia2))
* [jti_openconfig_telemetry](./plugins/inputs/jti_openconfig_telemetry)
* [kafka_consumer](./plugins/inputs/kafka_consumer)
* [kapacitor](./plugins/inputs/kapacitor)
* [aws kinesis](./plugins/inputs/kinesis_consumer) (Amazon Kinesis)
* [kernel](./plugins/inputs/kernel)
* [kernel_vmstat](./plugins/inputs/kernel_vmstat)
* [kibana](./plugins/inputs/kibana)
* [kubernetes](./plugins/inputs/kubernetes)
* [kube_inventory](./plugins/inputs/kube_inventory)
* [lanz](./plugins/inputs/lanz)
* [leofs](./plugins/inputs/leofs)
* [linux_sysctl_fs](./plugins/inputs/linux_sysctl_fs)
* [logparser](./plugins/inputs/logparser) (deprecated, use [tail](/plugins/inputs/tail))
* [logstash](./plugins/inputs/logstash)
* [lustre2](./plugins/inputs/lustre2)
* [mailchimp](./plugins/inputs/mailchimp)
* [marklogic](./plugins/inputs/marklogic)
* [mcrouter](./plugins/inputs/mcrouter)
* [memcached](./plugins/inputs/memcached)
* [mem](./plugins/inputs/mem)
* [mesos](./plugins/inputs/mesos)
* [minecraft](./plugins/inputs/minecraft)
* [modbus](./plugins/inputs/modbus)
* [mongodb](./plugins/inputs/mongodb)
* [monit](./plugins/inputs/monit)
* [mqtt_consumer](./plugins/inputs/mqtt_consumer)
* [multifile](./plugins/inputs/multifile)
* [mysql](./plugins/inputs/mysql)
* [nats_consumer](./plugins/inputs/nats_consumer)
* [nats](./plugins/inputs/nats)
* [neptune_apex](./plugins/inputs/neptune_apex)
* [net](./plugins/inputs/net)
* [net_response](./plugins/inputs/net_response)
* [netstat](./plugins/inputs/net)
* [nginx](./plugins/inputs/nginx)
* [nginx_plus_api](./plugins/inputs/nginx_plus_api)
* [nginx_plus](./plugins/inputs/nginx_plus)
* [nginx_upstream_check](./plugins/inputs/nginx_upstream_check)
* [nginx_vts](./plugins/inputs/nginx_vts)
* [nsq_consumer](./plugins/inputs/nsq_consumer)
* [nsq](./plugins/inputs/nsq)
* [nstat](./plugins/inputs/nstat)
* [ntpq](./plugins/inputs/ntpq)
* [nvidia_smi](./plugins/inputs/nvidia_smi)
* [openldap](./plugins/inputs/openldap)
* [openntpd](./plugins/inputs/openntpd)
* [opensmtpd](./plugins/inputs/opensmtpd)
* [openweathermap](./plugins/inputs/openweathermap)
* [pf](./plugins/inputs/pf)
* [pgbouncer](./plugins/inputs/pgbouncer)
* [phpfpm](./plugins/inputs/phpfpm)
* [phusion passenger](./plugins/inputs/passenger)
* [ping](./plugins/inputs/ping)
* [postfix](./plugins/inputs/postfix)
* [postgresql_extensible](./plugins/inputs/postgresql_extensible)
* [postgresql](./plugins/inputs/postgresql)
* [powerdns](./plugins/inputs/powerdns)
* [powerdns_recursor](./plugins/inputs/powerdns_recursor)
* [processes](./plugins/inputs/processes)
* [procstat](./plugins/inputs/procstat)
* [prometheus](./plugins/inputs/prometheus) (can be used for [Caddy server](./plugins/inputs/prometheus/README.md#usage-for-caddy-http-server))
* [puppetagent](./plugins/inputs/puppetagent)
* [rabbitmq](./plugins/inputs/rabbitmq)
* [raindrops](./plugins/inputs/raindrops)
* [redis](./plugins/inputs/redis)
* [rethinkdb](./plugins/inputs/rethinkdb)
* [riak](./plugins/inputs/riak)
* [salesforce](./plugins/inputs/salesforce)
* [sensors](./plugins/inputs/sensors)
* [sflow](./plugins/inputs/sflow)
* [smart](./plugins/inputs/smart)
* [snmp_legacy](./plugins/inputs/snmp_legacy)
* [snmp](./plugins/inputs/snmp)
* [snmp_trap](./plugins/inputs/snmp_trap)
* [socket_listener](./plugins/inputs/socket_listener)
* [solr](./plugins/inputs/solr)
* [sql server](./plugins/inputs/sqlserver) (microsoft)
* [stackdriver](./plugins/inputs/stackdriver) (Google Cloud Monitoring)
* [statsd](./plugins/inputs/statsd)
* [suricata](./plugins/inputs/suricata)
* [swap](./plugins/inputs/swap)
* [synproxy](./plugins/inputs/synproxy)
* [syslog](./plugins/inputs/syslog)
* [sysstat](./plugins/inputs/sysstat)
* [systemd_units](./plugins/inputs/systemd_units)
* [system](./plugins/inputs/system)
* [tail](./plugins/inputs/tail)
* [temp](./plugins/inputs/temp)
* [tcp_listener](./plugins/inputs/socket_listener)
* [teamspeak](./plugins/inputs/teamspeak)
* [tengine](./plugins/inputs/tengine)
* [tomcat](./plugins/inputs/tomcat)
* [twemproxy](./plugins/inputs/twemproxy)
* [udp_listener](./plugins/inputs/socket_listener)
* [unbound](./plugins/inputs/unbound)
* [uwsgi](./plugins/inputs/uwsgi)
* [varnish](./plugins/inputs/varnish)
* [vsphere](./plugins/inputs/vsphere) VMware vSphere
* [webhooks](./plugins/inputs/webhooks)
  * [filestack](./plugins/inputs/webhooks/filestack)
  * [github](./plugins/inputs/webhooks/github)
  * [mandrill](./plugins/inputs/webhooks/mandrill)
  * [papertrail](./plugins/inputs/webhooks/papertrail)
  * [particle](./plugins/inputs/webhooks/particle)
  * [rollbar](./plugins/inputs/webhooks/rollbar)
* [win_perf_counters](./plugins/inputs/win_perf_counters) (windows performance counters)
* [win_services](./plugins/inputs/win_services)
* [wireguard](./plugins/inputs/wireguard)
* [wireless](./plugins/inputs/wireless)
* [x509_cert](./plugins/inputs/x509_cert)
* [zfs](./plugins/inputs/zfs)
* [zipkin](./plugins/inputs/zipkin)
* [zookeeper](./plugins/inputs/zookeeper)

## Parsers

- [InfluxDB Line Protocol](/plugins/parsers/influx)
- [Collectd](/plugins/parsers/collectd)
- [CSV](/plugins/parsers/csv)
- [Dropwizard](/plugins/parsers/dropwizard)
- [FormUrlencoded](/plugins/parser/form_urlencoded)
- [Graphite](/plugins/parsers/graphite)
- [Grok](/plugins/parsers/grok)
- [JSON](/plugins/parsers/json)
- [Logfmt](/plugins/parsers/logfmt)
- [Nagios](/plugins/parsers/nagios)
- [Value](/plugins/parsers/value), ie: 45 or "booyah"
- [Wavefront](/plugins/parsers/wavefront)

## Serializers

- [InfluxDB Line Protocol](/plugins/serializers/influx)
- [JSON](/plugins/serializers/json)
- [Graphite](/plugins/serializers/graphite)
- [ServiceNow](/plugins/serializers/nowmetric)
- [SplunkMetric](/plugins/serializers/splunkmetric)
- [Carbon2](/plugins/serializers/carbon2)
- [Wavefront](/plugins/serializers/wavefront)

## Processor Plugins

* [clone](/plugins/processors/clone)
* [converter](/plugins/processors/converter)
* [date](/plugins/processors/date)
* [dedup](/plugins/processors/dedup)
* [enum](/plugins/processors/enum)
* [override](/plugins/processors/override)
* [parser](/plugins/processors/parser)
* [pivot](/plugins/processors/pivot)
* [printer](/plugins/processors/printer)
* [regex](/plugins/processors/regex)
* [rename](/plugins/processors/rename)
* [s2geo](/plugins/processors/s2geo)
* [strings](/plugins/processors/strings)
* [tag_limit](/plugins/processors/tag_limit)
* [template](/plugins/processors/template)
* [topk](/plugins/processors/topk)
* [unpivot](/plugins/processors/unpivot)

## Aggregator Plugins

* [basicstats](./plugins/aggregators/basicstats)
* [final](./plugins/aggregators/final)
* [histogram](./plugins/aggregators/histogram)
* [merge](./plugins/aggregators/merge)
* [minmax](./plugins/aggregators/minmax)
* [valuecounter](./plugins/aggregators/valuecounter)

## Output Plugins

* [influxdb](./plugins/outputs/influxdb) (InfluxDB 1.x)
* [influxdb_v2](./plugins/outputs/influxdb_v2) ([InfluxDB 2.x](https://github.com/influxdata/influxdb))
* [amon](./plugins/outputs/amon)
* [amqp](./plugins/outputs/amqp) (rabbitmq)
* [application_insights](./plugins/outputs/application_insights)
* [aws kinesis](./plugins/outputs/kinesis)
* [aws cloudwatch](./plugins/outputs/cloudwatch)
* [azure_monitor](./plugins/outputs/azure_monitor)
* [cloud_pubsub](./plugins/outputs/cloud_pubsub) Google Cloud Pub/Sub
* [cratedb](./plugins/outputs/cratedb)
* [datadog](./plugins/outputs/datadog)
* [discard](./plugins/outputs/discard)
* [elasticsearch](./plugins/outputs/elasticsearch)
* [exec](./plugins/outputs/exec)
* [file](./plugins/outputs/file)
* [graphite](./plugins/outputs/graphite)
* [graylog](./plugins/outputs/graylog)
* [health](./plugins/outputs/health)
* [http](./plugins/outputs/http)
* [instrumental](./plugins/outputs/instrumental)
* [kafka](./plugins/outputs/kafka)
* [librato](./plugins/outputs/librato)
* [mqtt](./plugins/outputs/mqtt)
* [nats](./plugins/outputs/nats)
* [nsq](./plugins/outputs/nsq)
* [opentsdb](./plugins/outputs/opentsdb)
* [prometheus](./plugins/outputs/prometheus_client)
* [riemann](./plugins/outputs/riemann)
* [riemann_legacy](./plugins/outputs/riemann_legacy)
* [socket_writer](./plugins/outputs/socket_writer)
* [stackdriver](./plugins/outputs/stackdriver) (Google Cloud Monitoring)
* [syslog](./plugins/outputs/syslog)
* [tcp](./plugins/outputs/socket_writer)
* [udp](./plugins/outputs/socket_writer)
* [warp10](./plugins/outputs/warp10)
* [wavefront](./plugins/outputs/wavefront)
