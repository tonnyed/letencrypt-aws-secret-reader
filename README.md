Parameter store variable reader
=========
This role reads aws_secret and aws_access_key_id from parameter store locally during deployment.
This value is used by let encrypt when setting up certificate 

Requirements
------------
Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------
A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

- input
  -  `secret_key_id(string)`: used to look parameter store aws_secret_key variable name 
  -  `secret_access(string)`: used to look parameter store aws_secret_access variable name 
  -  `aws_region(string)`: used to look parameter store aws_region variable name 
  -  `decrypt(bool):default=true`: used to look parameter store decrypt variable name
  -  `aws_profile(string)`: used to look parameter store aws_profile variable name
  -  `check_lookup(bool):default=false`: debugger to view the values returned from parameter store

- output
  - `aws_secret_access:` aws secret access fact returned from parameter store used by let-encrypt
  - `aws_secret_key_id:` aws secret key id fact returned form parameter store used by let-encrypt
Dependencies
------------
A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

These role depends on lets encrypt

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - letencrypt-aws-secret-reader
       vars
         - secret_key_id: "secret_key_id"
         - secret_access: "secret_access"
         - aws_region: "eu-west-2"
         - decrypt: true
         - aws_profile: "dev"
         - check_lookup: false

License
-------
BSD

Author Information
------------------
`tonnyed@hotmail.com`