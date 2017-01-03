certbot
=======

This role installs and configures [Certbot](https://certbot.eff.org/).

Role Variables
--------------

- `certbot_path`: Path to install certbot script (default: '/opt')
- `certbot_certs`: List of certificates to generate (default: Empty list)
- `certbot_auto_renew`: Set auto-renewal cronjob or not (default: True)
- `certbot_renew_hook`: Command to be executed when any certificate is renewed (Ex: 'service apache2 reload')
- `certbot_use_staging`: Use letsencrypt test server or not (default: False)
- `certbot_email`: Email used for registration and recovery contact (Ex: 'test@example.com')

Example Playbook
----------------

    - hosts: servers
      vars:
        certbot_certs:
          - auth_plugin: 'webroot'
            webroot_path: '/var/www/html'
            domains:
              - example.com
              - www.example.com
      roles:
        - {
          role: certbot,
          certbot_email: 'test@example.com'
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-certbot.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-certbot)
