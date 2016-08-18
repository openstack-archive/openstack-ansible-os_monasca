# OpenStack Ansible Monasca

An `openstack-ansible` compatible role for deploying the Monasca Monitoring-as-a-Service
feature to ECS OpenStack clouds.

## What It Installs

### Core Monasca Services

* `monasca-api`
* `monasca-persister`
* `monasca-notification`
* `monasca-thresh`
* `monasca-agent`
* `monasca-dashboard` (Horizon plugin)

### Additional Services

* `chrony`
* `zookeeper`
* `kafka`
* `storm`
* `influxdb`
* `grafana`

## Copyright

Copyright &copy; 2016 Internet Solutions (Pty) Ltd

## License

Licensed under the Apache Software License 2.0. See LICENSE for details.
