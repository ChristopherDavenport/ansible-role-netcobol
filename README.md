# NetCobol Installation For Linux

[![Build Status](https://travis-ci.org/ChristopherDavenport/ansible-role-netcobol.svg?branch=master)](https://travis-ci.org/ChristopherDavenport/ansible-role-netcobol)

This is proprietary software sold by Fujitsu and managed in America by
GTSoftware. You will first need to have the software. As it is extremely
illegal for me to distribute proprietary software. However this will
guide you through its installation smoothly.

The software is available as an rpm so I will attempt compatibility with
RedHat 7, Centos 7, RedHat 6, Centos 6, and Fedora.

First thing first is that this product has license controls built in
so first you will need to know the location of all the following rpm files.
-   `FJSVXcbrf-11.0.0-1.0.x86_64.rpm`
-   `FJSVXbsrt-7.0.0-3.0.x86_64.rpm`   
-   `FJSVXmeft-11.0.0-2.0.x86_64.rpm`
-   `FJSVXcbev-11.0.0-3.0.x86_64.rpm` 
-   `FJSVXrds-11.0.0-1.0.x86_64.rpm`
-   `FJSVXcbl-11.0.0-1.0.x86_64.rpm`   
-   `FJSVXcblf-11.0.0-1.0.x86_64.rpm`  
-   `FJSVXcbr-11.0.0-1.0.x86_64.rpm`   
-   `FJSVXcbre-11.0.0-1.0.x86_64.rpm`

If you already have the MAC address of the computer this is being 
installed on then please go and get your license file and designate
the path the to license file.

If you installed this via ansible galaxy then the default install location is
in /etc/ansible/roles/ChristopherDavenport.netcobol

## Requirements

None, it will make sure all dependencies are in place on
supported systems.

## Role Variables

Available variables are listed below, along with default values
(see ```defaults/main.yml```):

#### Failure Choices

If rpms are not present to be installed should the play fail. Default
is true because your aim is to install netcobol.

```
netcobol_fail_on_rpms: True
```

If license file is not present do we fail on its absence. Default is true
because without a license file netcobol will not work.

```
netcobol_fail_on_license: True
```

#### Netcobol RPM Management

The default location that rpms will be transfered to for the install.

```
netcobol_src_storage: /usr/local/src/netcobol
```

The default set of netcobol files to install on the system.

```
netcobol_files_to_install:
  - FJSVXcbrf-11.0.0-1.0.x86_64.rpm
  - FJSVXbsrt-7.0.0-3.0.x86_64.rpm
  - FJSVXmeft-11.0.0-2.0.x86_64.rpm
  - FJSVXcbev-11.0.0-3.0.x86_64.rpm
  - FJSVXrds-11.0.0-1.0.x86_64.rpm
  - FJSVXcbl-11.0.0-1.0.x86_64.rpm
  - FJSVXcblf-11.0.0-1.0.x86_64.rpm
  - FJSVXcbr-11.0.0-1.0.x86_64.rpm
  - FJSVXcbre-11.0.0-1.0.x86_64.rpm
```

#### Netcobol License Management

The local name of the license file incase you have multiple files and hence need
to pick individually per machine.

```
netcobol_local_license_file_name: license.txt
```

These final two are the location and name of the license file on the remote
machine as are expected by netcobol so only modify these if netcobol
drastically changes something.

```
netcobol_license_file_location: /etc/opt/NetCOBOL/
```

```
netcobol_remote_license_file_name: license.txt
```

## Dependencies

-   None

## Example Playbook

Although definitely add the files into the role files folder before attempting
to run this.

```
- hosts: appservers
  vars: 
    netcobol_files_to_install:
      - /path/to/rpms/FJSVXcbrf-11.0.0-1.0.x86_64.rpm
      - /path/to/rpms/FJSVXbsrt-7.0.0-3.0.x86_64.rpm
      - /path/to/rpms/FJSVXmeft-11.0.0-2.0.x86_64.rpm
      - /path/to/rpms/FJSVXcbev-11.0.0-3.0.x86_64.rpm
      - /path/to/rpms/FJSVXrds-11.0.0-1.0.x86_64.rpm
      - /path/to/rpms/FJSVXcbl-11.0.0-1.0.x86_64.rpm
      - /path/to/rpms/FJSVXcblf-11.0.0-1.0.x86_64.rpm
      - /path/to/rpms/FJSVXcbr-11.0.0-1.0.x86_64.rpm
      - /path/to/rpms/FJSVXcbre-11.0.0-1.0.x86_64.rpm
  roles:
    - ChristopherDavenport.netcobol
```

### License

MIT

### Author Information

This role was created in 2016 by ChristopherDavenport.
