breakfix2/SCENARIO_PERFORMANCE
=========

This role breaks the satellite by setting some large values to few of the satellite params.

What we essentially do by this ansible role is:

* Confirm that the satellite is running
* Set large values to puma max min threads, puma workers, foreman db pool, pulpcore workers


Requirements
------------

This ansible role requires the [foreman ansible modules](https://github.com/theforeman/foreman-ansible-modules/). Please install them before executing the role.

Role Variables
--------------

The `vars/main.yml` file contains the required variables for the ansible role. Adjust the values according to your environment.

Dependencies
------------

NA

Example Playbook
----------------

This ansible role can be executed after creating a playbook in the following way. 

~~~
# cat breakfix2.yaml
---
- name: Deploy ansible role breakfix2 on target systems
  hosts: satellite
  roles:
    - role: breakfix2
      tags: break
~~~

License
-------

It is free software licensed under the terms of the GNU General Public License GPL v3 or later. A copy of the license can be obtained here: http://www.gnu.org/licenses/gpl-3.0.html

Author Information
------------------

This role is developed by Soham Majumdar <smajumda@redhat.com>, <csedeepm@gmail.com>. 
