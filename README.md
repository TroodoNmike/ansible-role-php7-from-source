php7-from-source
=========

This role is going to install php7 from source. You can also include PHP-FPM and OPCache as optional. When both are enabled performance is amazing. When changing versions (upgrading/downgrading) it will recognize the change, download source code, recompile and deploy

    ansible-galaxy install TroodoNmike.php7-from-source


Variables to overwrite can be found in /defaults/main.yml:

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
