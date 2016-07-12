OpenStack-Ansible Heat
######################

Ansible role to install OpenStack Heat.

This role will install:
    * heat-api
    * heat-api-cfn
    * heat-api-cloudwatch
    * heat-engine

=================

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Required Variables
==================

To use this role, define the following variables:

.. code-block:: yaml
    # password of the keystone service user for heat
    heat_service_password: "secrete"
    # password of the admin user for the keystone heat domain
    heat_stack_domain_admin_password: "secrete"
    # key used for encrypting credentials stored in the heat db
    heat_auth_encryption_key: "32characterslongboguskeyvaluefoo"
    # password for heat database
    heat_container_mysql_password: "secrete"
    # password for heat RabbitMQ vhost
    heat_rabbitmq_password: "secrete"
    # comma-separated list of RabbitMQ hosts
    rabbitmq_servers: 10.100.100.101
    # Keystone admin user for service, domain, project, role creation
    keystone_admin_user_name: "admin"
    # Keystone admin password for service, domain, project, role creation
    keystone_auth_admin_password: "secrete"

Example Playbook
================
.. code-block:: yaml

    - name: Install heat server
      hosts: heat_all
      user: root
      roles:
        - { role: "os_heat", tags: [ "os-heat" ] }
      vars:
        external_lb_vip_address: 172.16.24.1
        internal_lb_vip_address: 192.168.0.1
        heat_galera_address: "{{ internal_lb_vip_address }}"
        keystone_admin_user_name: admin
        keystone_admin_tenant_name: admin

Tags
====

This role supports two tags: ``heat-install`` and ``heat-config``

The ``heat-install`` tag can be used to install and upgrade.

The ``heat-config`` tag can be used to manage configuration.
