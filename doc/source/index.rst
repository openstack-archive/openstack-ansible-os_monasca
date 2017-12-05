=========================
OpenStack-Ansible Monasca
=========================

.. toctree::
   :maxdepth: 2

   configure-monasca.rst

Ansible role for deploying Monasca Monitoring-as-a-Service.

This role installs the following Systemd services:

    * monasca-api
    * monasca-notification
    * monasca-persister
    * monasca-thresh

To clone or view the source code for this repository, visit the role repository
for `os_monasca <https://github.com/openstack/openstack-ansible-os_monasca>`_.

Default variables
~~~~~~~~~~~~~~~~~

.. literalinclude:: ../../defaults/main.yml
  :language: yaml
  :start-after: under the License.

Dependencies
~~~~~~~~~~~~

This role needs pip >= 7.1 installed on the target host.

Example playbook
~~~~~~~~~~~~~~~~

.. literalinclude:: ../../examples/playbook.yml
  :language: yaml

Tags
~~~~

This role supports the following tags:

    * ``monasca-install``: used to install and upgrade;
    * ``monasca-config``: used to manage configuration;
