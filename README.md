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

    java_version:           1.8
    minimum_heap_size:      512
    maximum_heap_size:      1024
    fcrepo_home:            "/etc/fcrepo/data"
    fcrepo_config_dir:      "/etc/fcrepo"
    fcrepo_log_dir:         "/var/log/fcrepo"
    fcrepo_major_version:   4
    fcrepo_version:         4.7.0
    fcrepo_url:             "https://github.com/fcrepo{{ fcrepo_major_version }}/fcrepo{{ fcrepo_major_version }}/releases/download/fcrepo-{{ fcrepo_version }}/fcrepo-webapp-{{ fcrepo_version }}.war"
    fcrepo_checksum_algo:   "sha1"
    fcrepo_checksum_url:    "{{ fcrepo_url }}.{{ fcrepo_checksum_algo }}"
    tomcat_install_dir:     "/usr/local"
    catalina_home:          "{{ tomcat_install_dir }}/tomcat"
    webapps_dir:            "{{ catalina_home }}/webapps"
    app_user:               "tomcat"
    java_opts:              "-Djava.awt.headless=true
                            -Dfile.encoding=UTF-8
                            -Dfcrepo.home={{ fcrepo_home }}
                            -Dfcrepo.modeshape.configuration=classpath:/config/file-simple/repository.json
                            -Dlogback.configurationFile={{ fcrepo_config_dir }}/logback.xml
                            -XX:+UseConcMarkSweepGC
                            -XX:+CMSClassUnloadingEnabled
                            -XX:ConcGCThreads=5
                            -XX:MaxGCPauseMillis=200
                            -XX:ParallelGCThreads=20
                            -XX:MaxMetaspaceSize=512M
                            -Xms{{ minimum_heap_size }}m
                            -Xmx{{ maximum_heap_size }}m"
    catalina_opts:          "-server"

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
