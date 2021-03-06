[![Build Status](https://travis-ci.org/TroodoNmike/ansible-role-php7-from-source.svg?branch=master)](https://travis-ci.org/TroodoNmike/ansible-role-php7-from-source)

php7-from-source
=========

This role is going to install php7 from source. You can also include PHP-FPM and OPCache as optional. When both are enabled performance is amazing. When changing versions (upgrading/downgrading) it will recognize the change, download source code, recompile and deploy

    ansible-galaxy install TroodoNmike.php7-from-source


Variables to overwrite can be found in /defaults/main.yml:

Usually you just need this:

    php_install_version: "7.0.8"


Example Playbook
----------------


    - hosts: servers
      roles:
         - { role: TroodoNmike.php7-from-source, php_install_version: "7.0.8" }

Or:

    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
         - { role: TroodoNmike.php7-from-source }

And in vars/main.yml include:

    php_install_version: "7.0.8"

When upgrading/downgrading simply change php_install_version value. For example from "7.0.7" to "7.0.8".

Make a note that every time you compile php it takes significant amount of time. The benefit is that you control exactly what version of php is on the server and you can easily upgrade/downgrade.

For faster compile times (where jobs=# is number of cpu cores used)

    php_source_make_command: "make --jobs=4"

Sometimes when you work with remote servers via ssh if one task (compiling php) takes long time to complete you may lose ssh connection. In this case I suggest adding into ansible.cfg settings:

    [ssh_connection]
    ssh_args = -o ServerAliveInterval=100 -o ControlMaster=auto -o ControlPersist=10m

Requirements
------------

Runs well with ubuntu/trusty64

Dependencies
------------

no dependencies

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
