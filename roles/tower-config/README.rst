tower-config
============

This role configures resources in Ansible Tower.

This documentation is a work in progress.

Variables
---------

For role defaults, see the ``defaults/main.yaml`` file.

- ``tower_config_no_log``: Toggles no_log on or off for tasks with sensitive information
- ``tower_config_verify_ssl``: Whether or not to verify the Tower SSL certificate
- ``tower_config_organizations``: A list of organizations
- ``tower_config_teams``: A list of teams
- ``tower_config_users``: A list of users
- ``tower_config_roles``: A list of roles
- ``tower_config_credentials``: A list of credentials
- ``tower_config_projects``: A list of projects
- ``tower_config_inventories``: A list of inventories
- ``tower_config_inventory_sources``: A list of inventory sources
- ``tower_config_job_templates``: A list of job templates
