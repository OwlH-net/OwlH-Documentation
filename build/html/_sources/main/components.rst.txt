Components
==========


.. image:: /img/architecture_block.png


OwlH will help to integrate and manage multiple NIDS solutions, providing a centralized management solution. To accomplish this, we deploy different components.

OwlH provides flexibility and scalability to be integrated with 3rd party solutions as Moloch for forensics and many others. You can grow as needed in your network. 



OwlH Master
-----------

Is an appliance running the centralized management API. All centralized stuff happens here. configurations, synchronizations.

:doc:`see more about OwlH Master<OwlHMaster>`

OwlH Node 
---------

Is an appliance that will include NIDS software as Suricata and/or Zeek. This appliance will be able to listen network traffic, analyze it and forward analysis results to an storage and visualization platform like ELK or Splunk.
It also helps with network traffic transport in our Software TAP configuration

:doc:`see more about OwlH Node<OwlHNode>`


OwlH UI
-------

The graphical User Interface that will provide an easy access and visualization of all management capabilities

:doc:`see more about OwlH User Interface<OwlHUI>`


OwlH Client
-----------

Small and light weight client used to transport traffic from servers to an OwlH Node or OwlH Master when there is no way to access directly network traffic, ex. Cloud environments.

:doc:`see more about OwlH Client<OwlHClient>`



.. _Github repos: https://github.com/owlh-net
Check our `Github repos`_

