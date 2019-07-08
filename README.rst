ansible-tower-cicd
==================

A framework for continuous integration and continuous delivery with Ansible Tower.

It installs Tower and uses Tower to update itself with this repository.

.. image:: docs/source/_static/screenshot.png

Disclaimer
==========

Please note that this community project is not officially supported by Red Hat.

What does it do ?
=================

This repository allows you to deploy Ansible Tower and manage it's resources
automatically through version controlled configuration.

After doing the initial bootstrap deployment, Ansible Tower will keep itself
up to date automatically by re-running the setup and configuration playbooks
against itself based on the latest code from this repository.

What is supported ?
===================

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
- `Schedules <https://github.com/dmsimard/ansible-tower-cicd/blob/master/library/tower_schedule.py>`_

Usage
=====

tl;dr::

    # Deploys Tower on localhost with defaults on a vanilla RHEL or CentOS server
    git clone https://github.com/dmsimard/ansible-tower-cicd
    cd ansible-tower-cicd

    # Install dependencies
    ./dependencies.sh

    # Install Tower itself
    ansible-playbook -i inventory.yaml playbooks/tower-setup.yaml

    # Configure Tower for the first time
    ansible-playbook playbooks/tower-config.yaml

    # Tower will now keep itself up to date using this repository

As necessary, supply your own configuration as extra-vars to override the role
defaults.

Activating the Ansible Tower License
====================================

By default, the ``tower-setup`` role will not attempt to activate a license and
Ansible Tower will prompt you for a license the first time you log in to the
instance.

If you'd like to activate the license automatically, set
``tower_setup_license_configure`` to ``True`` and supply a json license in-line
for the variable ``tower_setup_license``.

Known issues
============

- It is not possible to attach more than one credential to job templates: https://github.com/ansible/ansible/issues/43234
- Activating a license automatically requires users to add ``"eula_accepted": true`` manually to their JSON license file.
- Module failures on "tower_verify_ssl" parameter: https://github.com/ansible/ansible/commit/77e01e6abc67efe4056924c620281f29a42c0159

Troubleshooting
===============

``no_log`` is enabled by default for tasks that configure Tower resources in
the ``tower-config`` role because they could otherwise print sensitive
information to the console.

If you're troubleshooting errors with that role, you can disable ``no_log``
by setting the variable ``tower_config_no_log`` to ``False`` to help you see
what is being sent and received.

Contributors
============

See contributors on GitHub_.

.. _GitHub: https://github.com/dmsimard/ansible-tower-cicd/graphs/contributors

Copyright
=========

::

    Copyright (c) 2018 Red Hat, Inc.

    ansible-tower-cicd is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    ansible-tower-cicd is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with ansible-tower-cicd.  If not, see <http://www.gnu.org/licenses/>.
