Role Name
=========

Installs and configures the Fedora Commons repository platform
WIP - very minimal thus far

Requirements
------------

Java 8
Tomcat 7 or later

NOTE: Fedora can run on any servlet 3.0 container, including Jetty 9.x or later.
However, this role only supports Tomcat at this time.

Role Variables
--------------

TBD

Dependencies
------------

See Requirements

Example Playbook
----------------

    - hosts: fedora
      become: true

      roles:
      - { role: java }
      - { role: tomcat }
      - { role: fedora-commons }

License
-------

CC0

Author Information
------------------

Drew Heles
