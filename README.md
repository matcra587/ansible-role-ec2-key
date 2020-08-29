EC2 Key Management
==================

![Ansible Lint](https://github.com/matcra587/ansible-role-ec2-key/workflows/Ansible%20Lint/badge.svg)

A role to manage the EC2 Keys used to connect to Linux EC2 Instances, or decrypt Windows Admin Passwords.

Requirements
------------

The below requirements are needed on the host that executes Ansible.

* boto
* boto3
* python >= 2.6

A SSH key is required on the host that executes Ansible.

Role Variables
--------------

| Variable | Type | Default Value |
| :--- | :--- | --- |
| `aws_access_key` | string | *omit* |
| `aws_region` | string | eu-west-1 |
| `aws_secret_key` | string | *omit* |
| `aws_security_token` | string | *omit* |
| `key_name` | string | |
| `overwrite_key` | boolean | false |
| `public_key` | string | ~/.ssh/id_rsa.pub |
| `remove_key` | boolean | false |

Valid AWS credentials **must** be specified either by setting `aws_access_key` and `aws_secret_key` variables or by defining `AWS_ACCESS_KEY` and `AWS_SECRET_KEY` environment variables.

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Create new EC2 Key
      hosts: localhost
      connection: local
      roles:
         - role: ansible-role-ec2-key
           key_name: Special Key
           public_key: ~/.ssh/id_rsa.pub
           overwrite_key: false

    - name: Update existing new EC2 Key
      hosts: localhost
      connection: local
      roles:
         - role: ansible-role-ec2-key
           key_name: Special Key
           public_key: ~/.ssh/id_ed25519.pub
           overwrite_key: true

    - name: Remove existing EC2 Key
      hosts: localhost
      connection: local
      roles:
         - role: ansible-role-ec2-key
           key_name: Special Key
           remove_key: false

License
-------

[MIT](LICENSE)

Author Information
------------------

Matt Craven
