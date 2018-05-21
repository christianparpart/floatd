# Floatd

A fluentd alternative using Flow Language.

An imaginary feature list could look like that:

- Data Sources
  - file
  - syslog
  - UNIX domain socket
  - UDP
  - TCP
  - HTTP
  - SNMP
- Data Sinks
  - file
  - ElasticSearch
  - Kafka
  - mySQL
  - Graphite
  - Librato
  - Statsd
  - SMTP
  - Slack
  - IRC
- Builtin API functions
  - `string urldecode(string)`
  - `string geoip.city(ip)`
  - `string geoip.country_code(ip)`
  - `string geoip.country_name(ip)`
  - `string geoip.postal_code(ip)`
  - `void retag(string new_tag)`
  - ...
