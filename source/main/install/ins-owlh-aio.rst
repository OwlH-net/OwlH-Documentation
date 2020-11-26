Install OwlH - all-in-one
=========================

Choose your platform: 
---------------------

+-------------------------------------------------+----------------------------------+
| Linux Distribution                              | Repository                       | 
+=================================================+==================================+
| CentOS 7                                        | repo.owlh.net/current-centos     |
+-------------------------------------------------+----------------------------------+
| Debian/Ubuntu                                   | repo.owlh.net/current-debian     |
+-------------------------------------------------+----------------------------------+
| Raspbidian                                      | repo.owlh.net/current-arm        |
+-------------------------------------------------+----------------------------------+

Download OwlHInstaller: 
-----------------------

.. note:: 

   Please be sure you choose the right repo 

.. tabs::

  .. group-tab:: CENTOS

    .. code-block:: console
       
       # cd /tmp
       # wget repo.owlh.net/current-centos/owlhinstaller.tar.gz
       # mkdir owlhinstaller
       # tar -C /tmp/owlhinstaller/ -xf /tmp/owlhinstaller.tar.gz

  .. group-tab:: DEBIAN/UBUNTU

    .. code-block:: console
       
       # cd /tmp
       # wget repo.owlh.net/current-debian/owlhinstaller.tar.gz
       # mkdir owlhinstaller
       # tar -C /tmp/owlhinstaller/ -xf /tmp/owlhinstaller.tar.gz




Verify OwlH Installer configuration: 
------------------------------------

Verify your owlhinstaller configuration file for repository, action and targets.

configuration file: ``/tmp/owlhinstaller/config.json``

.. tabs::

  .. group-tab:: CENTOS

    .. code-block:: console
       
        "action": "install",                                 <<< this should be install 
        "repourl":"http://repo.owlh.net/current-centos/",    <<< be sure to us the right repository
        "target": [
            "owlhmaster",                                     /
            "owlhnode",                                      <   As we want to install an AIO
            "owlhui"                                          \
        ],

  .. group-tab:: DEBIAN/UBUNTU

    .. code-block:: console
       
        "action": "install",                                 <<< this should be install 
        "repourl":"http://repo.owlh.net/current-debian/",    <<< be sure to us the right repository
        "target": [
            "owlhmaster",                                     /
            "owlhnode",                                      <   As we want to install an AIO
            "owlhui"                                          \
        ],



Run OwlH Installer:
-------------------

run owlh installer 

.. code-block:: console
   
   # cd /tmp/owlhinstaller
   # ./owlhinstaller


After executed you should and output like this:

  .. code-block:: none
   :class: output

        2020/11/24 08:21:31.095 [I]  OwlH Installer - v0.17.2.20201031
        2020/11/24 08:21:31.112 [I]  Downloading http://repo.owlh.net/current-centos/current.version to /tmp/current.version
        2020/11/24 08:21:31.112 [I]  == MASTER ==
        2020/11/24 08:21:31.112 [I]  PRESCRIPTS - MASTER -> owlhmasterprescripts/
        2020/11/24 08:21:31.112 [I]  Master INSTALL
        2020/11/24 08:21:31.112 [I]  Downloading New Software
        2020/11/24 08:21:31.701 [I]  ManageMaster Stopping the service
        2020/11/24 08:21:31.701 [I]  owlhmaster systemd stopping...
        2020/11/24 08:21:31.711 [I]  ManageMaster Copying files from download
        2020/11/24 08:21:31.711 [I]  SRC: /tmp/owlhmaster/owlhmaster -- DST: /usr/local/owlh/src/owlhmaster/owlhmaster
        2020/11/24 08:21:32.020 [I]  ManageMaster Installing service...
        2020/11/24 08:21:32.193 [I]  ManageMaster Copying current.version...
        2020/11/24 08:21:32.193 [I]  SRC: /tmp/current.version -- DST: /usr/local/owlh/src/owlhmaster/conf/current.version
        2020/11/24 08:21:32.195 [I]  ManageMaster Launching service...
        2020/11/24 08:21:32.195 [I]  owlhmaster systemd starting...
        2020/11/24 08:21:32.220 [I]  ManageMaster Done!
        2020/11/24 08:21:32.220 [I]  POSTSCRIPTS - MASTER -> owlhmasterpostscripts/
        2020/11/24 08:21:32.235 [I]  Files removed for owlhmaster successfully!
        2020/11/24 08:21:32.235 [I]  == NODE ==
        2020/11/24 08:21:32.235 [I]  PRESCRIPTS - NODE -> owlhnodeprescripts/
        2020/11/24 08:21:32.235 [I]  Node INSTALL
        2020/11/24 08:21:32.235 [I]  Downloading New Software
        2020/11/24 08:21:33.822 [I]  ManageNode Stopping the service
        2020/11/24 08:21:33.822 [I]  owlhnode systemd stopping...
        2020/11/24 08:21:33.952 [I]  ManageNode Copying files from download
        2020/11/24 08:21:33.952 [I]  SRC: /tmp/owlhnode/owlhnode -- DST: /usr/local/owlh/src/owlhnode/owlhnode
        2020/11/24 08:21:34.242 [I]  SRC: /tmp/current.version -- DST: /usr/local/owlh/src/owlhnode/conf/current.version
        2020/11/24 08:21:34.244 [I]  ManageNode Installing service...
        2020/11/24 08:21:34.383 [I]  ManageNode Launching service...
        2020/11/24 08:21:34.384 [I]  owlhnode systemd starting...
        2020/11/24 08:21:34.414 [I]  ManageNode Done!
        2020/11/24 08:21:34.414 [I]  POSTSCRIPTS - NODE -> owlhnodepostscripts/
        2020/11/24 08:21:34.436 [I]  Files removed for owlhnode successfully!
        2020/11/24 08:21:34.436 [I]  == UI ==
        2020/11/24 08:21:34.436 [I]  PRESCRIPTS - UI -> owlhuiprescripts/
        2020/11/24 08:21:34.436 [I]  New Install for UI
        2020/11/24 08:21:34.436 [I]  Downloading New Software
        2020/11/24 08:21:34.686 [I]  ManageUI Copying files from download
        2020/11/24 08:21:35.521 [I]  ManageUI Launching service...
        2020/11/24 08:21:35.521 [I]  SRC: /tmp/current.version -- DST: /var/www/owlh/conf/current.version
        2020/11/24 08:21:35.524 [I]  owlhui OwlH UI - systemd starting...
        2020/11/24 08:21:36.614 [I]  ManageUI Done!
        2020/11/24 08:21:36.614 [I]  POSTSCRIPTS - UI -> owlhuipostscripts/
        2020/11/24 08:21:36.630 [I]  Files removed for owlhui successfully!

Output may vary 


Install and configure httpd/apache server side
----------------------------------------------

you must install httpd/apache and the owlh site configuration file. 


.. tabs::

  .. group-tab:: CENTOS

    .. code-block:: console
       
       # cd /tmp/
       # wget repo.owlh.net/current-centos/services/owlhui-httpd.sh
       # bash owlhui-httpd.sh 1.1.1.1

  .. group-tab:: DEBIAN/UBUNTU

    .. code-block:: console
           
           # cd /tmp/
           # wget repo.owlh.net/current-debian/services/owlhui-httpd.sh
           # bash owlhui-httpd.sh 1.1.1.1

where: 

   :1.1.1.1: is your master ip. 

you can edit your master ip on file /var/www/owlh/conf/ui.conf

Install suricata
----------------

If you want to use Suricata. You will configure Suricata from UI mostly


.. tabs:: 

  .. group-tab:: CENTOS

    .. code-block:: console
       
       # cd /tmp/
       # wget repo.owlh.net/current-centos/services/owlhsuricata.sh
       # bash owlhsuricata.sh

  .. group-tab:: DEBIAN/UBUNTU

    .. code-block:: console
       
       # cd /tmp/
       # wget repo.owlh.net/current-debian/services/owlhsuricata.sh
       # bash owlhsuricata.sh




Install Zeek
------------

This step can take a long while, consider running it under a screen session.

.. tabs::

  .. group-tab:: CENTOS

    .. code-block:: console
       
       # cd /tmp/
       # wget repo.owlh.net/current-centos/services/owlhzeek.sh
       # bash owlhzeek.sh

  .. group-tab:: DEBIAN/UBUNTU

    .. code-block:: console
       
       # cd /tmp/
       # wget repo.owlh.net/current-debian/services/owlhzeek.sh
       # bash owlhzeek.sh



Install OwlH Interface
----------------------

If you plan to use Software TAP configuration, you should prepare your owlh local interface

.. tabs::

  .. group-tab:: CENTOS

    .. code-block:: console
       
       # cd /tmp/
       # wget repo.owlh.net/current-centos/services/owlhinterface.sh
       # bash owlhinterface.sh

  .. group-tab:: DEBIAN/UBUNTU
    .. code-block:: console 
      modprobe -v dummy numdummies=2
      ip link add owlh type dummy
      ip link set owlh mtu 65535
      ip link set owlh up

    Save this commands to an /rc.local script


Also, if using suricata and Software TAP you will need to add this interface details to af-packet: key

Edit /etc/suricata/suricata.yaml and add: 

.. code-block:: console

  af-packet:
    - interface: owlh
      #threads: auto
      cluster-id: 98
      cluster-type: cluster_flow
      defrag: yes
      #rollover: yes
      #use-mmap: yes
      #mmap-locked: yes
      tpacket-v3: yes
      ring-size: 2048
      block-size: 409600
      #block-timeout: 10
      #use-emergency-flush: yes
      #checksum-checks: kernel
      #bpf-filter: port 80 or udp
      #copy-mode: ips
      #copy-iface: eth1



Verify everything is properly set
---------------------------------


.. code-block:: console

  # netstat -nputa 

should provide an output like this:

.. code-block:: console

    [root@ip-172-31-41-217 ec2-user]# netstat -nputa
    Active Internet connections (servers and established)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
    ...
    tcp6       0      0 :::443                  :::*                    LISTEN      2570/httpd
    ... 
    tcp6       0      0 :::50001                :::*                    LISTEN      2451/owlhmaster
    ...
    tcp6       0      0 :::50002                :::*                    LISTEN      9936/owlhnode


Now you should be able to access your master with your browser. 
