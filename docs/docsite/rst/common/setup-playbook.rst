.. index::
   pair: installation script; playbook setup
   single: playbook setup
   pair: playbook setup; setup.sh

AWX setup playbook can be run directly without the need for the ``./setup.sh`` script. You should use the playbook directly to configure AWX.

The setup playbook can be executed as follows:

::

    ansible-playbook -i INVENTORY_FILE -e EXTRA_VARS setup.yml

The setup playbook accepts the following arguments:

- ``-i INVENTORY_FILE`` -- Path to Ansible inventory file (default: ``inventory``)
- ``-e EXTRA_VARS`` -- Set additional Ansible variables as key=value or YAML/JSON (i.e., ``-e bundle_install=false`` forces an online installation)
- ``-b`` -- Perform a database backup in lieu of installing
- ``-r`` -- Perform a database restore in lieu of installing (a default restore path is used unless EXTRA_VARS are provided with a non-default path, as shown in the code example below)

For restoring the database:

::

    ansible-playbook -i INVENTORY_FILE -e 'restore_backup_file=/path/to/nondefault/location' -e 'restore=yes' setup.yml
