breakfix1
=========

This role targets to break a satellite and capsule server in a way that, neither hosts will be able to download patches from them nor any repos can be successully resynced on the satellite. 

Example Error:

Status code: 500  when trying to install\update packages on the RHEL systems connected with the satellite server through a capsule server.

~~~
[MIRROR] katello-host-tools-4.2.3-5.el8sat.noarch.rpm: Status code: 500 for https://capsule.example.com/pulp/content/RedHat/Library/content/dist/layered/rhel8/x86_64/sat-client/6/os/Packages/k/katello-host-tools-4.2.3-5.el8sat.noarch.rpm (IP: XX.XX.XXX.XXX)
~~~

What we essentially do by this ansible role is:

* Confirm that the satellite is running
* Create an activation key
* Generate a registration command [ via Global registration method ] to register a host through the external capsule server
* Execute the command on the client and register it
* Update database records of satellite and capsule to break them.


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

This role is developed by Sayan Das <saydas@redhat.com>, <connectwithsayan03@gmail.com>. 
