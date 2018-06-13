# rsyslog-formula
[![Build Status](https://travis-ci.org/ssplatt/rsyslog-formula.svg?branch=master)](https://travis-ci.org/ssplatt/rsyslog-formula)

configure rsyslog. TLS server and client modes are available with both tcp and udp.

Formula changed around so that the /etc/rsyslog.com file doesn't get changed as much. Configurations are instead written to /etc/rsyslog.d/<name>.conf. These files are generated by the rsyslog.configs hash. The file written out is the more usuable 'Rainer' script. It's a little easier to automate, but seems like it's missing some docs. 

The formula generates 'enough' of a configuration to allow running as a server and as a client.

### Defaults
```
rsyslog:
  enabled: False
  required_pkgs:
    - rsyslog
  service:
    name: rsyslog
    state: running
    enable: True
  tls:
    enable: False
```
## Server and Client with TLS
```
rsyslog:
  enabled: True
  service:
    name: rsyslog
    state: running
    enable: True
  configs:
    # see pillar example
  tls:
    enable: True
    ca_dir: '/etc/pki/example_test_ca'
    ca_file: 'example_test_ca_ca_cert.crt'
    cert_dir: '/etc/pki/example_test_ca/certs'
    cert_file: '{{ grains.host }}.crt'
    key_dir: '/etc/pki/example_test_ca/certs'
    key_file: '{{ grains.host}}.key'
```
## Basic Server and Client over TCP
```
rsyslog:
  enabled: True
  service:
    name: rsyslog
    state: running
    enable: True
  configs:
    # see pillar example
```
## Basic Server and Client over UDP
```
rsyslog:
  enabled: True
  service:
    name: rsyslog
    state: running
    enable: True
  configs:
    # see pillar example
```
