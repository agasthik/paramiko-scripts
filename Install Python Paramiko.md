##The instructions below have been tested to work on RHEL 6,7.

###As root user, first install epel repo (Required for Python-pip)

```

[root@ak-lab-2 vagrant]# wget --no-check-certificate https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
--2016-10-08 15:53:28--  https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
Resolving proxy.mycompany.com (proxy.mycompany.com)... 159.45.22.175
Connecting to proxy.mycompany.com (proxy.mycompany.com)|159.45.22.175|:80... connected.
WARNING: cannot verify dl.fedoraproject.org's certificate, issued by ‘/C=US/O=My Company/OU=My Company Certification Authorities/CN=My Company Bluecoat ProxySG Certification Authority 02 G2’:
  Self-signed certificate encountered.
Proxy request sent, awaiting response... 200 OK
Length: 14612 (14K) [application/x-rpm]
Saving to: ‘epel-release-latest-7.noarch.rpm’

100%[==================================================================================================>] 14,612      --.-K/s   in 0.04s

2016-10-08 15:53:29 (370 KB/s) - ‘epel-release-latest-7.noarch.rpm’ saved [14612/14612]

[root@ak-lab-2 vagrant]# yum install epel-release-latest-7.noarch.rpm
.cache/                           .config/                          epel-release-latest-7.noarch.rpm  .ssh/
[root@ak-lab-2 vagrant]# yum install epel-release-latest-7.noarch.rpm
Loaded plugins: langpacks, rhnplugin
This system is receiving updates from RHN Classic or Red Hat Satellite.
Examining epel-release-latest-7.noarch.rpm: epel-release-7-8.noarch
Marking epel-release-latest-7.noarch.rpm to be installed
Resolving Dependencies
--> Running transaction check
---> Package epel-release.noarch 0:7-8 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

============================================================================================================================================
 Package                         Arch                      Version                   Repository                                        Size
============================================================================================================================================
Installing:
 epel-release                    noarch                    7-8                       /epel-release-latest-7.noarch                     24 k

Transaction Summary
============================================================================================================================================
Install  1 Package

Total size: 24 k
Installed size: 24 k
Is this ok [y/d/N]: y
Downloading packages:
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Warning: RPMDB altered outside of yum.
  Installing : epel-release-7-8.noarch                                                                                                  1/1
  Verifying  : epel-release-7-8.noarch                                                                                                  1/1

Installed:
  epel-release.noarch 0:7-8

Complete!

```

###Install the various OS packages and then install python paramiko. 
#####Some of these packages may already be installed on your system
```
yum install gcc libffi-devel python-devel openssl-devel python-pip
pip install paramiko
```

###If you are behind a proxy export the variables on command line and then run the `pip install paramiko` command

```
export https_proxy=http://user:password@proxyhost:proxyport
export http_proxy=http://user:password@proxyhost:proxyport
```
================================================

#####Sample Execution is per below

```
[root@ak-lab-2 vagrant]# yum install -y gcc libffi-devel python-devel openssl-devel python-pip
Loaded plugins: langpacks, rhnplugin
This system is receiving updates from RHN Classic or Red Hat Satellite.
Package gcc-4.8.5-4.el7.x86_64 already installed and latest version
Package 1:openssl-devel-1.0.1e-51.el7_2.1.x86_64 already installed and latest version
Resolving Dependencies
--> Running transaction check
---> Package libffi-devel.x86_64 0:3.0.13-16.el7 will be installed
---> Package python-devel.x86_64 0:2.7.5-34.el7 will be installed
---> Package python-pip.noarch 0:7.1.0-1.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================================================================================
 Package                            Arch                         Version                             Repository                                            Size
================================================================================================================================================
Installing:
 libffi-devel                       x86_64                       3.0.13-16.el7                       rhel-x86_64-7.2.eus-2016.01-OS                        23 k
 python-devel                       x86_64                       2.7.5-34.el7                        rhel-x86_64-7.2.eus-2016.01-OS                       391 k
 python-pip                         noarch                       7.1.0-1.el7                         epel                                          1.5 M

Transaction Summary
================================================================================================================================================
Install  3 Packages

Total download size: 1.9 M
Installed size: 7.7 M
Downloading packages:
(1/3): libffi-devel-3.0.13-16.el7.x86_64.rpm                                                                                             |  23 kB  00:00:00
(2/3): python-devel-2.7.5-34.el7.x86_64.rpm                                                                                              | 391 kB  00:00:00
python-pip-7.1.0-1.el7.noarch.rpm                                                                                                        | 1.5 MB  00:00:00

Total                                                                                                                           1.5 MB/s | 1.9 MB  00:00:01
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : libffi-devel-3.0.13-16.el7.x86_64                                                                                                            1/3
  Installing : python-pip-7.1.0-1.el7.noarch                                                                                                                2/3
  Installing : python-devel-2.7.5-34.el7.x86_64                                                                                                             3/3
  Verifying  : python-devel-2.7.5-34.el7.x86_64                                                                                                             1/3
  Verifying  : python-pip-7.1.0-1.el7.noarch                                                                                                                2/3
  Verifying  : libffi-devel-3.0.13-16.el7.x86_64                                                                                                            3/3

Installed:
import paramiko
  libffi-devel.x86_64 0:3.0.13-16.el7                   python-devel.x86_64 0:2.7.5-34.el7                   python-pip.noarch 0:7.1.0-1.el7

Complete!

[root@ak-lab-2 vagrant]# export https_proxy=http://proxy.mycompany.com
[root@ak-lab-2 vagrant]# export http_proxy=http://proxy.mycompany.com
[root@ak-lab-2 vagrant]# pip install paramiko
You are using pip version 7.1.0, however version 8.1.2 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Collecting paramiko
  Downloading paramiko-2.0.2-py2.py3-none-any.whl (171kB)
    100% |████████████████████████████████| 172kB 841kB/s
Collecting pyasn1>=0.1.7 (from paramiko)
  Downloading pyasn1-0.1.9-py2.py3-none-any.whl
Collecting cryptography>=1.1 (from paramiko)
  Downloading cryptography-1.5.2.tar.gz (400kB)
    100% |████████████████████████████████| 401kB 709kB/s
Collecting idna>=2.0 (from cryptography>=1.1->paramiko)
  Downloading idna-2.1-py2.py3-none-any.whl (54kB)
    100% |████████████████████████████████| 57kB 7.1MB/s
Requirement already satisfied (use --upgrade to upgrade): six>=1.4.1 in /usr/lib/python2.7/site-packages (from cryptography>=1.1->paramiko)
Collecting setuptools>=11.3 (from cryptography>=1.1->paramiko)
  Downloading setuptools-28.2.0-py2.py3-none-any.whl (467kB)
    100% |████████████████████████████████| 471kB 668kB/s
Collecting enum34 (from cryptography>=1.1->paramiko)
  Downloading enum34-1.1.6-py2-none-any.whl
Collecting ipaddress (from cryptography>=1.1->paramiko)
  Downloading ipaddress-1.0.17-py2-none-any.whl
Collecting cffi>=1.4.1 (from cryptography>=1.1->paramiko)
  Downloading cffi-1.8.3.tar.gz (403kB)
    100% |████████████████████████████████| 405kB 598kB/s
Collecting pycparser (from cffi>=1.4.1->cryptography>=1.1->paramiko)
  Downloading pycparser-2.14.tar.gz (223kB)
    100% |████████████████████████████████| 225kB 1.8MB/s
Installing collected packages: pyasn1, idna, setuptools, enum34, ipaddress, pycparser, cffi, cryptography, paramiko
  Found existing installation: setuptools 0.9.8
    Uninstalling setuptools-0.9.8:
      Successfully uninstalled setuptools-0.9.8
  Running setup.py install for pycparser
  Running setup.py install for cffi
  Running setup.py install for cryptography
Successfully installed cffi-1.8.3 cryptography-1.5.2 enum34-1.1.6 idna-2.1 ipaddress-1.0.17 paramiko-2.0.2 pyasn1-0.1.9 pycparser-2.14 setuptools-28.2.0
```
