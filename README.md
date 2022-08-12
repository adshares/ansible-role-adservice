<p align="center">
    <a href="https://adshares.net/" title="Adshares sp. z o.o." target="_blank">
        <img src="https://adshares.net/logos/ads.svg" alt="Adshares" width="100" height="100">
    </a>
</p>
<h3 align="center"><small>Adshares / Adservice Ansible role</small></h3>
<p align="center">
    <a href="https://github.com/adshares/ansible-role-adservice/issues/new?template=bug_report.md&labels=Bug">Report bug</a>
    ·
    <a href="https://github.com/adshares/ansible-role-adservice/issues/new?template=feature_request.md&labels=New%20Feature">Request feature</a>
    ·
    <a href="https://github.com/adshares/ansible-role-adservice/wiki">Wiki</a>
</p>

Adshares adservice
=========

Installs and configures the Adshares adserver with all necessary modules.

Requirements
------------

- Domain with 3 subdomains for AdServer, AdPanel and AdUser (default `app.`, `panel.` and `au.`) directed to the server.

Role Variables
--------------

    service_name

**Required**. Available services: `adserver`, `adpanel`, `adselect`, `aduser`, `adpay`, `adcontroller`.

    setup: false

Enables installation and configuration of libraries and packages necessary for the service.

    deploy: false

Enables the deployment or update of the service.

    server_domain: localhost

Domain of publicly available services (AdServer, AdPanel, AdController, AdUser) - e.g. *example.com*

    adserver_prefix: app

AdServer module domain prefix (subdomain) - e.g. *app.example.com*

    adpanel_prefix: panel

AdPanel module domain prefix (subdomain) - e.g. *panel.example.com*

    aduser_prefix: au

AdUser module domain prefix (subdomain) - e.g. *au.example.com*

    use_certbot: true

Enables the use of certbot (for Let's Encrypt).

    vendor_dir: /opt/adshares

Service installation folder.

    log_dir: /var/log/adshares

Service logs folder.

    service_user: adshares

Service installation username.

    repo_version: master

Service code version.

    clean_after_days: 7

The period of keeping old version files.

Dependencies
------------

- [nickhammond.logrotate](https://github.com/nickhammond/ansible-logrotate)

Example Playbook
----------------

Installing all modules:

    - hosts: servers
      roles:
        - role: adshares.adservice
          vars:
            service_name: "{{ item }}"
            server_domain: example.com
            setup: true
            deploy: true
          loop:
            - adserver
            - adpanel
            - adselect
            - aduser
            - adpay
            - adcontroller

Updating all modules:

    - hosts: servers
      roles:
        - role: adshares.adservice
          vars:
            service_name: "{{ item }}"
            deploy: true
          loop:
            - adserver
            - adpanel
            - adselect
            - aduser
            - adpay
            - adcontroller

License
-------

This work is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This work is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
[GNU General Public License](LICENSE) for more details.

You should have received a copy of the License along with this work.
If not, see <https://www.gnu.org/licenses/gpl.html>.

Author Information
------------------

* **[Maciej Pilarczyk](https://github.com/m-pilarczyk)** - _Programmer_
* **[Paweł Podkalicki](https://github.com/PawelPodkalicki)** - _Programmer_

See also the list of [contributors](https://github.com/adshares/ansible-role-adservice/contributors) who participated in this project.
