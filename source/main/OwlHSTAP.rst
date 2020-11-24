Software TAP 
============

Transport traffic from remote instances to a central OwlH Node or OwlH Master. Traffic will be analyzed on OwlH Node by Suricata, Zeek and OwlH Analyzer, or will be dispatched between multiple OwlH Nodes by OwlH Master.

This scenario is valid on Cloud environments as well as any site without SPAN or MIRROR port availability

components:

  :owlh node: should be installed and ready - check :doc:`install OwlH Node </main/install/ins-owlh-aio>`
  :owlh client: will be installed on any server you want to collect traffic from.

configure owlh node for STAP
----------------------------

* Verify owlh interface is set 

.. code-block:: console

  # ip a
    ...
    3: owlh: <BROADCAST,NOARP,UP,LOWER_UP> mtu 65535 qdisc noqueue state UNKNOWN group default qlen 1000
        link/ether 2a:a3:de:a0:fd:76 brd ff:ff:ff:ff:ff:ff
        inet6 fe80::28a3:deff:fea0:fd76/64 scope link
           valid_lft forever preferred_lft forever


* Suricata and Zeek must be configured to listen to owlh interface

Check from your UI, your node configuration for Suricata and Zeek, both must be listening to owlh interface.

* Configure software TAP server from UI 

:: 

  from UI
    - From nodes -> node services configuration -> Software TAP
    - Create a Socket to Network STAP server 
    - Set a Name
    - Select the interface owlh from interface list 
    - let default Cert file
    - let default port (50010)

Add service.

* Start software TAP server from UI 

Just click Start and check that STAP server is on and running. Keep this screen open as we will see here the clients that are connected to the new STAP server.

.. note::

  more than one STAP server can be configured, you only need to set a different port where new server will be listening.


prepare your instances 
----------------------

What is OwlH Client?
--------------------

OwlH client is an small client that runs in end point platforms and it will forward traffic in real-time to a central Software TAP server.

This OwlH client is useful when you are running OwlH in any Software TAP configuration. Mostly, it is used in Cloud environments when you want to forward traffic from your instance to an OwlH Node for analysis, but also can be run on deployments where an SPAN or Mirror port are not available.

**OwlH Client is currently available for:**


:CentOS: https://repo.owlh.net/current-centos/owlhclient.sh
:Debian/Ubuntu: https://repo.owlh.net/current-debian/owlhclient.sh


.. Attention::

    **Windows users**

    You can manage your STAP client configuration running following command

    ::
        

        C:\windump\windump -i 1 -nn -s0 -w - not port 50010| C:\cygwin64\bin\socat  - OPENSSL:192.168.142.149:50010,cert=/usr/local/certs/ca.pem,verify=0,forever,retry=0,interval=5

    To be able to run this in a windows 2012 R2 or newer you will need few packets. 

    * Windump and wimpcap
    * Socat (installed with Cygwin) 


* Download and Install 

.. code-block:: console

  # wget repo.owlh.net/current-centos/owlhclient.sh
  # bash owlhclient.sh


OwlH Client will be installed on 
  
::

  /usr/local/owlh/bin/

.. note::

    Configuration file and log files (one log file per interface) are in the same folder.


Configuration file conf.json looks like this: 

::

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

Be sure to update the parameters properly. 


:Collector IP: Is your OwlH Node or OwlH Master IP that is running the STAP socket-to-network service
:Collector Port: Is the port on OwlH StAP service side 
:Cert: Is deployed and build with the sh script when installing client. feel free to change as needed. 
:BPF: Please, take care here. as you are forwarding traffic from a host to a different one, you can create a loop or kill your network if forwarding is not right filtered. minimum filtering must include STAP service ports like in the picture
:Include Interfaces: This parameter allows you to define which interfaces client must listen to. current configuration will manage enX (en0, en1, en2 etc) as well as ethX (eth0, eth1, eth2 etc). A log file for each interface will be created. 
:Exclude Interfaces: Lets suppose you don't want to listen to en1 as per our previous sample, then you can include here en1 as an interface to exclude. 
:Include Nets: You will also able to filter what interfaces to listen by identifying with ip and network has the interface defined. 0.0.0.0/0 means that any ip is allowed. 
:Exclude IPs: Again, you can stop collecting from interfaces that will include the excluded ip. 
:Wait Time: Time between checks in minutes. if you do a configuration change, Client will restart as needed with the new configuration. If client went down or connection is lost because OwlH STAP service is done for a while, Client will try to reconnect each 'wait time'


* start it

.. code-block:: console

    # systemctl daemon-reload 
    # systemctl enable owlhstap
    # systemctl start owlhstatp


Verify your client is connected. 
--------------------------------

* from UI 
* from shell 

