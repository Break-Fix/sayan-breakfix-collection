breakfix0/SCENARIO_LEAPP
=========

This role registers a RHEL8 client to satellite and simulates few problems while performing the LEAPP upgrade to RHEL9.

What we essentially do by this ansible role is:

* Confirm that the satellite is running
* Create an activation key
* Create and publish content view without the RHEL9 minor repos
* Generate a registration command [ via Global registration method ] to register the client to satellite
* Execute the command on the client and register it
* Configure EPEL on client and install openssl rpms from it.


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
# cat breakfix0.yaml
---
- name: Deploy ansible role breakfix0 on target systems
  hosts: satellite
  roles:
    - role: breakfix0
      tags: break
~~~

License
-------

It is free software licensed under the terms of the GNU General Public License GPL v3 or later. A copy of the license can be obtained here: http://www.gnu.org/licenses/gpl-3.0.html

Author Information
------------------

This role is developed by Soham Majumdar <smajumda@redhat.com>, <csedeepm@gmail.com>. 
