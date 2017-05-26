=======================================================
Configuring the Monitoring (monasca) service (optional)
=======================================================

.. note::

   This feature is experimental at this time and it has not been fully
   production tested yet.

Monasca is an open-source multi-tenant, highly scalable, performant,
fault-tolerant monitoring-as-a-service solution that integrates with
OpenStack. It uses a REST API for high-speed metrics processing and
querying and has a streaming alarm engine and notification engine.

Monasca is configured using the ``/etc/openstack_deploy/conf.d/monasca.yml``
file and the ``/etc/openstack_deploy/user_variables.yml`` file.

Configuring target hosts
~~~~~~~~~~~~~~~~~~~~~~~~

Modify ``/etc/openstack_deploy/conf.d/monasca.yml`` by adding a list
containing the infrastructure target hosts for the ``monasca-infra_hosts``
and its required services:

In ``monasca.yml``:

   .. code-block:: yaml

       monasca-infra_hosts:
         infra01:
           ip: INFRA01_IP_ADDRESS
         infra02:
           ip: INFRA02_IP_ADDRESS
         infra03:
           ip: INFRA03_IP_ADDRESS

       monasca-zookeeper_hosts:
         infra01:
           ip: INFRA01_IP_ADDRESS
         infra02:
           ip: INFRA02_IP_ADDRESS
         infra03:
           ip: INFRA03_IP_ADDRESS

       monasca-kafka_hosts:
         infra01:
           ip: INFRA01_IP_ADDRESS
         infra02:
           ip: INFRA02_IP_ADDRESS
         infra03:
           ip: INFRA03_IP_ADDRESS

       monasca-influxdb_hosts:
         infra01:
           ip: INFRA01_IP_ADDRESS
         infra02:
           ip: INFRA02_IP_ADDRESS
         infra03:
           ip: INFRA03_IP_ADDRESS


Replace ``*_IP_ADDRESS`` with the IP address of the br-mgmt container
management bridge on each target host.

This hosts will be used to deploy the containers where monasca and its
required services will be installed.

Setting up Monasca
~~~~~~~~~~~~~~~~~~

Run the setup-hosts playbook, to create the monasca containers, and the
repo-build playbook to update the repository with the monasca packages:

   .. code-block:: console

       # cd /opt/openstack-ansible/playbooks
       # openstack-ansible setup-hosts.yml
       # openstack-ansible repo-build.yml

Run the monasca and horizon playbooks to install monasca and enable the
Monitoring panel in horizon:

   .. code-block:: console

       # cd /opt/openstack-ansible/playbooks
       # openstack-ansible os-monasca-install.yml
       # openstack-ansible os-horizon-install.yml

Monitoring Hosts
~~~~~~~~~~~~~~~~

To start monitoring, monasca requires the monasca-agent to be deployed on
the hosts which will be monitored. The monasca-agent deployment and
configuration is covered by the `monasca-agent role`_.

.. _monasca-agent role: https://github.com/openstack/openstack-ansible-os_monasca-agent
