repo-extra
========

An [ansible role](https://galaxy.ansibleworks.com/list#/roles/202) to install the
[rpmfusion](http://rpmfusion.org) free, nonfree, and
[livna](http://rpm.livna.org/) yum repositories which contain extra software
packages [not available](https://fedoraproject.org/wiki/Forbidden_items) in the
standard Fedora repositories.

After enabling the role you must explicitly install the packages you want:

    ---
    - hosts: localhost

      roles:
        - groks.repo-extra

      tasks:
        - name: install packages not in the main fedora repos
          yum: name={{ item }} state=present
          with_items:
            - gstreamer-plugins-bad
            - freetype-freeworld
            - libdvdcss
            - VirtualBox

Get a list of the available packages by running the following command:

    yum --disablerepo="*" \
        --enablerepo="rpmfusion-free,rpmfusion-nonfree,livna" \
        list available | grep -v i686

Requirements
------------

An installation of Fedora.

Role Variables
--------------

None.

Dependencies
------------

None.

License
-------

BSD
