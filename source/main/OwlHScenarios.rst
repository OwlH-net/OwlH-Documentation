OwlH Scenarios and main configurations
======================================

Software TAP Scenario
---------------------

components:

  * owlh node - should be installed and ready
  * owlh client - will be installed on any server you want to collect traffic from.

configure owlh node
-------------------

* verify owlh interface is set 

.. code-block:: console

  3: owlh: <BROADCAST,NOARP,UP,LOWER_UP> mtu 65535 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether 2a:a3:de:a0:fd:76 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::28a3:deff:fea0:fd76/64 scope link
       valid_lft forever preferred_lft forever


* Suricata and Zeek must be configured to listen to owlh interface
* Configure software TAP server from UI 
* Start software TAP server from UI 

prepare your instances 
----------------------

* download and install owlh client

remember to choose the right repository depending on your client distribution.

+-------------------------------------------------+----------------------------------+
| Linux Distribution                              | Repository                       | 
+=================================================+==================================+
| CentOS 7                                        | repo.owlh.net/current-centos     |
+-------------------------------------------------+----------------------------------+
| Debian/Ubuntu                                   | repo.owlh.net/current-debian     |
+-------------------------------------------------+----------------------------------+
| Raspbidian                                      | repo.owlh.net/current-arm        |
+-------------------------------------------------+----------------------------------+


.. code-block:: console

  # wget repo.owlh.net/current-centos/owlhclient.sh
  # bash owlhclient.sh

* check client configuration 

a client configuration will include interface to listen to, exclusions, remote Software TAP Server or collector, bpf filter, ... be sure to configure the right options. 

.. code-block:: console

  {
      "collectorIP":"10.13.1.13",
      "collectorPort":"50010",
      "cert":"/usr/local/owlh/src/owlhnode/conf/certs/ca.pem",
      "bpf":"not port 50010 and not port 22",
      "includeInt":["en","eth"],
      "excludeInt":["lo"],
      "includeNet":["0.0.0.0/0"],
      "excludeIP":["192.168.0.1"],
      "waitTime":10
  }




* start it

Verify your client is connected. 
--------------------------------

* from UI 
* from shell 

