OwlH Node
=========


What is OwlH Node?
------------------

This is a single box running your NIDS systems, by default it will run Suricata and Zeek.
While you do your local analysis with your Suricata and Zeek, you can also do things like:

* Forward sniffed traffic in real time to a different system 
* Collect traffic from remote servers sent by socket and save it to PCAP files or re-inject that traffic to a local network interface
* Include threat intelligence feeds and analyze your suricata and zeek outputs. 

About Network Sniffing
----------------------

SPAN port or Port Mirror
^^^^^^^^^^^^^^^^^^^^^^^^

Usually you will deploy this component with two network interfaces. Interface #1 will be management interface and interface #2 will be the sniffing interface. This interface #2 will be connected to the SPAN port or port mirror. 

The SPAN port should be configured to forward a replica of all your network traffic through it. Be sure you have configured the SPAN port properly to forward the right traffic.

Install it 
----------
      * :doc:`Install OwlH</main/OwlHInstall>` 



