gitlab-ansible
=========

Small Ansible role  for provisionning Gitlab behind an Apache2 

Requirements
------------

You should have a {{gitlab_user}} present, with a home  on your target host 

Role Variables
--------------

{{gitlab_domain}} I use to set it in my inventory file as a host var.

Dependencies
------------

No other role dependecy

Example Playbook
----------------


    - hosts: gitlab_servers
      roles:
         - { role: radamanth.gitlab-ansible, x: 42 }

License
-------

GPL V2

Author Information
------------------
I've been a computer science engineer for more than 10 years now, I've discovered Ansible in 2014, and fell in love with it.
I use it in my company to manage different server since then. 
Feel free to visit our site www.neovia.fr 

I'm also one of the founder of Immozeo, where Ansible is also greatly used.

www.immozeo.com
