Legomac
=======

See `My LEGO Macintosh Classic with Raspberry Pi and e-paper display
<http://beenje.github.io/blog/posts/my-lego-macintosh-classic-with-raspberry-pi-and-e-paper-display>`_
and `Experimenting with asyncio on a Raspberry Pi
<http://beenje.github.io/blog/posts/experimenting-with-asyncio-on-a-raspberry-pi>`_

Lego Digital Designer
---------------------

The LEGO building instructions can be found under the `ldd` directory.

Ansible playbooks
-----------------

This repository includes 2 playbooks:

- epd-demo.yml (to install a simple Clock demo)
- playbook.yml (to install `aiolegomac <https://github.com/beenje/aiolegomac>`_)

Roles variables
~~~~~~~~~~~~~~~

::

    traefik_image: beenje/traefik
    aiolegomac_image: beenje/aiolegomac
    pigpiod_image: beenje/pigpiod
    traefik_network: traefik-network
    traefik_debug: "false"
    # Accepted values, in order of severity: "DEBUG", "INFO", "WARN", "ERROR", "FATAL", "PANIC"
    traefik_log_level: ERROR
    traefik_dashboard_port: 8080
    traefik_domain: example.com
    traefik_letsencrypt_email: ""
    # Use the let's encrypt staging server by default
    # Set to true to use the production environment
    traefik_letsencrypt_production: false

    aiolegomac_port: 7777
    aiolegomac_network: aiolegomac-network
    aiolegomac_hostname: legomac.example.com
    aiolegomac_username: username
    aiolegomac_password: password
    aiolegomac_jwt_secret: secret
    aiolegomac_jwt_exp_delta_seconds: 604800
    aiolegomac_timezone: 'Europe/Stockholm'

Usage
~~~~~

Clone the repository::

    $ git clone https://github.com/beenje/legomac.git
    $ cd legomac

Edit the `hosts` file to set the hostname of your Raspberry Pi.
Create a `host_vars/<hostname>` file to modify the needed variables.

Run the playbook::

    $ ansible-playbook -i hosts -k playbook.yml


Note that the `epd-demo.yml` playbook doesn't include any variables.
