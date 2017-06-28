fast-vm-import-images
=====================

This role imports images for fast-vm.

Requirements
------------

This roles was tested only on CentOS/RHEL 7.3. On RHEL systems this role expects that system is properly registered so it can download and install packages.
Also the working fast-vm installation is expected to be present on the machine

Role Variables
--------------

  - URL or local path base to location where XML files are located
    ```
    xml_url_base: 'https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master'

    ```

  - URL or local path base to location where hack files are located
    ```
    hacks_url_base: 'https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master'
    ```

  - URL base of public fast-vm images mirror or local path to fast-vm images
    ```
    public_image_url_base: 'http://ftp.linux.cz/pub/linux/people/ondrej_famera/fastvm-images'
    ```

  - URL base of RHEL fast-vm images mirror or local path to fast-vm RHEL images
    ```
    rhel_image_url_base: ''
    ```

Example Playbook
----------------

Import all (except of RHEL) images from default mirror.

    - hosts: servers
      roles:
         - { role: OndrejHome.fast-vm-import-images }


Import everything from from local drive (offline import, no Internet connection required).

    - hosts: servers
      roles:
         - { role: OndrejHome.fast-vm-import-images, rhel_image_url_base: '/local/path/to/rhel/images', public_image_url_base: '/local/path/to/public/images', xml_url_base: '/local/path', hacks_url_base: '/local/path' }


**IMPORTANT** By default this role imports _all_ available images. To select which images you want to import use 'tags'.
Example of importing centos 6 BIOS images, centos 7 UEFI images and fedora 25 image.

    # ansible-playbook example.yml --tags 'centos6,centos7_uefi,fedora25'

License
-------

GPLv3

Author Information
------------------

To get in touch with author you can use email ondrej-xa2iel8u@famera.cz or create a issue on github when requesting feature(s).
