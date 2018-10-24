library
=======

We might need to carry patches until they've been landed and released in 
upstream Ansible.

Doing so should be documented so that we can eventually stop carrying them.

+------------------------+-----------------------------------------------+
| **module**             | **reason**                                    |
+------------------------+-----------------------------------------------+
| tower_job_template     | Picked up from devel due to changing API_     |
+------------------------+-----------------------------------------------+
| tower_schedule         | Not yet upstream                              |
+------------------------+-----------------------------------------------+

.. _API: https://github.com/ansible/ansible/issues/43234
