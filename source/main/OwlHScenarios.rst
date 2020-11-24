OwlH Scenarios and main configurations
======================================

Software TAP Scenario
---------------------

components:

  * owlh node 
  * owlh client

prepare owlh node
------------------

* owlh interface is set 

.. code-block:: console

  3: owlh: <BROADCAST,NOARP,UP,LOWER_UP> mtu 65535 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether 2a:a3:de:a0:fd:76 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::28a3:deff:fea0:fd76/64 scope link
       valid_lft forever preferred_lft forever


* Suricata and Zeek must be configured to listen to owlh interface
* configure software TAP server from UI 
* start software TAP server from UI 

prepare your instances 
----------------------

* download and install owlh client
* check client configuration 
* start it

Verify your client is connected. 
--------------------------------

* from UI 
* from shell 

