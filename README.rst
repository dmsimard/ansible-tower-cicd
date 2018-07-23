ansible-tower-cicd
==================

A framework for continuous integration and continuous delivery with Ansible Tower.

It installs Tower and uses Tower to update itself with this repository.

.. image:: docs/source/_static/screenshot.png

*Please note that this is a work in progress.*

What does it do ?
-----------------

This repository allows you to deploy Ansible Tower and manage it's resources
automatically through version controlled configuration.

After doing the initial bootstrap deployment, Ansible Tower will keep itself
up to date automatically by re-running the setup and configuration playbooks
against itself based on the latest code from this repository.

What is supported ?
-------------------

The following are currently supported and automated:

- Ansible Tower installation
- License activation (with `tower-cli <https://github.com/ansible/tower-cli>`_)
- `Organizations <https://docs.ansible.com/ansible/devel/modules/tower_organization_module.html>`_
- `Teams <https://docs.ansible.com/ansible/devel/modules/tower_team_module.html>`_
- `Users <https://docs.ansible.com/ansible/devel/modules/tower_user_module.html>`_
- `Roles <https://docs.ansible.com/ansible/devel/modules/tower_role_module.html>`_
- `Credentials <https://docs.ansible.com/ansible/devel/modules/tower_credential_module.html>`_
- `Projects <https://docs.ansible.com/ansible/devel/modules/tower_project_module.html>`_
- `Inventories <https://docs.ansible.com/ansible/devel/modules/tower_inventory_module.html>`_
- `Inventory sources <https://docs.ansible.com/ansible/devel/modules/tower_inventory_source_module.html>`_
- `Job templates <https://docs.ansible.com/ansible/devel/modules/tower_job_template_module.html>`_

Usage
-----

As necessary, supply your own configuration for the ``inventory.yaml`` file
as well as the ``tower-setup`` role and ``tower-config`` role.

Install dependencies by running ``dependencies.sh`` and then run::

    ansible-playbook playbooks/tower-setup.yaml
    ansible-playbook playbooks/tower-config.yaml
