Ansible Role: Fedora Commons
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

    fcrepo_required_java_version:           1.8
    fcrepo_minimum_heap_size:      512
    fcrepo_maximum_heap_size:      1024
    fcrepo_home:            "/etc/fcrepo/data"
    fcrepo_config_dir:      "/etc/fcrepo"
    fcrepo_log_dir:         "/var/log/fcrepo"
    fcrepo_major_version:   4
    fcrepo_version:         4.7.1
    fcrepo_download_url:    "https://github.com/fcrepo{{ fcrepo_major_version }}/fcrepo{{ fcrepo_major_version }}/releases/download/fcrepo-{{ fcrepo_version }}/fcrepo-webapp-{{ fcrepo_version }}.war"
    fcrepo_checksum_algo:   "sha1"
    fcrepo_checksum_url:    "{{ fcrepo_download_url }}.{{ fcrepo_checksum_algo }}"
    fcrepo_tomcat_service_user: "{{ tomcat_service_user | default('tomcat') }}"
    fcrepo_catalina_home:   "/usr/share/tomcat8"
    fcrepo_catalina_base:   "/var/lib/tomcat8"
    fcrepo_webapps_dir:     "{{ fcrepo_catalina_base }}/webapps"

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

