=================
Table of Contents
=================

.. toctree::
   :maxdepth: 2

   overview.rst

Required Variables
~~~~~~~~~~~~~~~~~~

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

To clone or view the source code for this repository, visit the role repository
for `os_heat <https://github.com/openstack/openstack-ansible-os_heat>`_.

Default variables
~~~~~~~~~~~~~~~~~

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Example playbook
~~~~~~~~~~~~~~~~

.. literalinclude:: ../../examples/playbook.yml
   :language: yaml

Tags
~~~~

This role supports two tags: ``heat-install`` and
``heat-config``. The ``heat-install`` tag can be used to install
and upgrade. The ``heat-config`` tag can be used to maintain the
configuration of the service.
