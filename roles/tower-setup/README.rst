tower-setup
===========

This role installs Ansible Tower.

This documentation is a work in progress.

Variables
---------

For role defaults, see the ``defaults/main.yaml`` file.

**Retrieving and running the ansible-tower-setup script**:

- ``tower_setup_basename``: Name of the ansible-tower-setup script
- ``tower_setup_version``: Version of Ansible Tower to install
- ``tower_setup_archive``: File name of the ansible-tower-setup archive
- ``tower_setup_release_url``: URL to download the ansible-tower-setup archive from
- ``tower_setup_inventory_file``: Path where the Ansible Tower inventory will be written to
- ``tower_setup_inventory``: Literal Ansible Tower inventory (in YAML)

**Setting up the Ansible Tower license**:

- ``tower_setup_license_configure``: Whether or not to attempt to activate a license
- ``tower_setup_license_file``: Path to the license file on the control node filesystem

**tower-cli**:

- ``tower_setup_cli_config``: A dictionary containing the tower-cli configuration
