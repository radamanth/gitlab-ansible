gitlab-ansible
=========

Small Ansible role  for provisionning Gitlab behind an Apache2 

Requirements
------------

You should have a {{gitlab_user}} present, with a home  on your target host 

Role Variables
--------------

{{gitlab_domain}} I personnaly set it in my inventory file as a host var.

Defaults vars : 

```YAML
# User use by gitlab. See template configruation file. This user must exist in your system.
gitlab_user: "gitlab"

# gitlab user group. See template configruation file.
gitlab_group: "gitlab"

# Where to find the debian package 
gitlab_package_url: "https://downloads-packages.s3.amazonaws.com/ubuntu-14.04/gitlab_7.9.2-omnibus-1_amd64.deb"

# unicorn porn use by gitlab 
gitlab_port: "8042"
# mail gitlab will use when mailing notifications
gitlab_admin_mail: "youmail@yourdomain.com"

# General config.
gitlab_external_url: "https://{{gitlab_domain}}/"
gitlab_internal_url: "http://127.0.0.1:{{gitlab_port}}/"

gitlab_git_data_dir: "/home/{{gitlab_user}}/gitlab"
gitlab_public_dir: "{{ gitlab_git_data_dir }}/public"

# SSL Configuration.
gitlab_ssl_certificate: "/etc/gitlab/ssl/gitlab.crt"
gitlab_ssl_certificate_key: "/etc/gitlab/ssl/gitlab.key"

# SSL Self-signed Certificate Configuration.
gitlab_create_self_signed_cert: true
gitlab_self_signed_cert_subj: "/C=FR/ST=France/L=Toulouse/O=IT/CN={{gitlab_domain}}"

# Feel free to modify
gitlab_init_root_passwd: "ThisShouldBeYourLittleSecretPassword"

# PID file location
gitlab_pidfile: "/opt/gitlab/var/unicorn/unicorn.pid"

# To let apache2 do things with gitlab
gitlab_external_user: "www-data"

# Gitlab groups to create see http://doc.gitlab.com/ce/api/groups.html for optional fields
gitlab_groups: 
  - { "name": "Foobar Group",
    "path": "foo-bar",
    "description": "This is an awesome description" }
    
# list of users to create see http://doc.gitlab.com/ce/api/users.html for optinal fields
# email (required) - Email
# password (required) - Password
# username (required) - Username
# name (required) - Name
gitlab_users:
  - { "username": "john_smith",
  "email": "john@example.com",
  "password": "secret1",
  "name": "John Smith" }
  - { "username": "bob_flanagan",
  "email": "bob@example.com",
  "password": "secret2",
  "name": "Bob Flanagan"}

# List of gitlabt project to initialize, see http://doc.gitlab.com/ce/api/projects.html for optional fields 
gitlab_projects: 
  - { "name": "foo" }

```

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
