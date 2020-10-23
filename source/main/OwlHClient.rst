OwlH Client
===========

What is OwlH Client?
--------------------

OwlH client is an small app that runs in end points platforms and it will be helpful to forward traffic in real-time or store it locally until it is collected or is time to forward.

This OwlH client is useful when you are running OwlH in any Software TAP configuration. Mostly, it is used in Cloud environments when you want to forward traffic from your instance to an OwlH Node for analysis.

Install 
-------

**Currently OwlH Client is available for: **

::

    CentOS -> repo.owlh.net/current-centos/owlhclient.sh
    Debian/Ubuntu -> repo.owlh.net/current-debian/owlhclient.sh


.. Attention::

    **For Windows users**

    You can manage your STAP client configuration running following command

    ::
        

        C:\windump\windump -i 1 -nn -s0 -w - not port 50010| C:\cygwin64\bin\socat  - OPENSSL:192.168.142.149:50010,cert=/usr/local/certs/ca.pem,verify=0,forever,retry=0,interval=5

    To be able to run this in a windows 2012 R2 or newer you will need few packets. 

    * Windump and wimpcap
    * Socat (installed with Cygwin) 


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


* **Collector IP** - is you OwlH Node or OwlH Master IP that is running the STAP socket-to-network service
* **Collector Port** - is the port on OwlH StAP service side 
* **Cert** - is deployed and build with the sh script when installing client. feel free to change as needed. 
* **BPF** - Please, take care here. as you are forwarding traffic from a host to a different one, you can create a loop or kill your network if forwarding is not right filtered. minimum filtering must include STAP service ports like in the picture
* **Include Interfaces** - This parameter allows you to define which interfaces client must listen to. current configuration will manage enX (en0, en1, en2 etc) as well as ethX (eth0, eth1, eth2 etc). A log file for each interface will be created. 
* **Exclude Interfaces** - lets suppose you don't want to listen to en1 as per our previous sample, then you can include here en1 as an interface to exclude. 
* **Include Nets** - You will also able to filter what interfaces to listen by identifying with ip and network has the interface defined. 0.0.0.0/0 means that any ip is allowed. 
* **Exclude IPs** - again you can stop collecting from interfaces that will include the excluded ip. 
* **Wait Time** - Time between checks in minutes. if you do a configuration change, Client will restart as needed with the new configuration. If client went down or connection is lost because OwlH Stap service is done for a while, Client will try to reconnect each 'wait time'