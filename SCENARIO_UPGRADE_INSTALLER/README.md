breakfix1/SCENARIO_UPGRADE
=========

This role simulates some problems while doing a satellite upgrade.

What we essentially do by this ansible role is:

* Confirm that the satellite is running
* Change the IP in /etc/hosts
* Replace hostname -f with shortname
* Set incorrect tuning param in /etc/foreman-installer/scenarios.d/satellite.yaml
* Create a repo file in /etc/yum.repos.d/ as the rh-cloud.repo.


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
# cat breakfix1.yaml
---
- name: Deploy ansible role breakfix1 on target systems
  hosts: satellite
  roles:
    - role: breakfix1
      tags: break
~~~

License
-------

It is free software licensed under the terms of the GNU General Public License GPL v3 or later. A copy of the license can be obtained here: http://www.gnu.org/licenses/gpl-3.0.html

Author Information
------------------

This role is developed by Soham Majumdar <smajumda@redhat.com>, <csedeepm@gmail.com>. 
