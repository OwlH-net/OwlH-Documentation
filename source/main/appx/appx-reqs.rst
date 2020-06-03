Appendix - Requirements
=======================

Prepare your environment
------------------------

Traffic capture 
^^^^^^^^^^^^^^^
**OwlH Node - 1G - traffic monitor**

.. image:: /img/1G.png

**OwlH Node - 10G - traffic monitor**

.. image:: /img/10g.png


Capture configuration - interfaces
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  * Be sure you have at least one local interface connected to a SPAN or MIRROR PORT. This can work on physical and virtual appliances. 
  * Also, some configurations will use an internal dummy interface named owlh for using with Software TAP configurations. Be sure interface MTU is set to 65535.

Operating systems 
-----------------

OS versions support
^^^^^^^^^^^^^^^^^^^^^^^

.. note::

  You may need some help to find binaries, please be in contact with us to find the right configuration for your OS if you can't find your deployment option


Supported

  * CentOS 7, 8
  * Ubuntu 16, 18

Tested

  * Debian
  * RHEL 7, 8
  * ARM Raspbidian
  * FreeBSD and HardenedBSD


OS sizing
^^^^^^^^^
  * Check requirements based on traffic analysis needs for RAM, CPU and Storage.
  * Take care about storage, please size this paths as needed, be sure your rotation policies keep folders clean or configure rotation using OwlH log file rotation capability: 
      * /var/log/suricata folder is used by Suricata.
      * /var/log/owlh folder is used by OwlH analyzer and API logs.
      * /usr/local/zeek folder is used by Zeek.
      * /data/moloch is used by Moloch. Take care, PCAP files usually are heavy and may require some TB to allow you the right retention period.

Master 

.. image:: /img/master.png