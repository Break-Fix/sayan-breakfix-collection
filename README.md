# To develop breakfix scenarios for a Red Hat Satellite based infrastructure.

## Author, Copyright and License
This project is initiated by Sayan Das <saydas@redhat.com>, <connectwithsayan03@gmail.com>. It is free software licensed under the terms of the GNU General Public License GPL v3 or later. A copy of the license can be obtained here: http://www.gnu.org/licenses/gpl-3.0.html

## Motivation!

Basic training sessions on individual topics of Red Hat Satellite is not good enough to make someone a good **Administrator of Red Hat Satellite** or **Support Engineer for Red Hat Satellite** product. It's important to understand 
* How the product works in the backend
* How end-users are using it in their own environments
* What types of problems are being reported by the end-users
* And most importantly
    - How to investigate them ?
    - What data to ask for ?
    - What logs files to inspect ?
    - How to find out a suitable solution to fix the problem ?
    
The breakfix modules are developed by combining real-world examples with support-team's experiences and our goal is to make sure that, the audience slowly starts understanding the objectives mentioned earlier, while going through the different modules.


## Things covered in this project
The project would consist of individual ansible roles for individual breakfix modules that we plan to develop. It's recommended to read through the **README.md** file of individual ansible roles to understand their usage and purposes.

## Compatibility
The roles were tested to be working with Satellite Version 6.14 and later.

## Prerequisites

#### Note: It's recommended to have some basic **Ansible** and **Red Hat Satellite** knowledge to operate and use this project.

* Make sure to have a standard Red Hat Satellite + Capsule deployment and one or more RHEL systems build to act as client systems. 

* Make sure that each of those systems have the following commands executed.

   ~~~
   # useradd ec2-user;
   # echo 'ec2-user:password@123' | /usr/sbin/chpasswd;
   # echo "ec2-user   ALL=NOPASSWD:   ALL" | tee -a /etc/sudoers.d/ec2-user;
   ~~~

* Determine your bastion\master system and make sure that the master system can talk to the Satellite\Capsule\RHEL-Clients over SSH using the ec2-user without any password. 


## How to use

* Fork the project and clone it in your master\bastion node.

* Copy `ansible.cfg.example` by name `ansible.cfg` and make changed in the file as per your requirements.

* Create an `inventory` file e.g. 

   ~~~
   # cat inventory
   [localhost]
   127.0.0.1 ansible_connection=local ansible_become=false

   [satellite]
   satellite615.lab.example.com
   
   [capsule]
   capsule615.lab.example.com

   [client]
   rhel8.lab.example.com
   ~~~

* **IMPORTANT!** Edit the `requirements.yml` file to ensure all required collections are part of this file. And then install the collections using this command i.e. 

   ~~~
   # ansible-galaxy install -r requirements.yml
   ~~~
   
* Refer to the **README.md** and `vars/main.yml` of each ansible role and make sure all the pre-requisites have been fulfilled e.g. installation of additional ansible modules or updating the variable values.

* Execute the roles in the following way i.e. 

   ~~~
   # ansible-playbook -i inventory breakfix1.yaml
   ~~~



## Contributions
Contributions are very welcome :-) Just send me a pull-request


