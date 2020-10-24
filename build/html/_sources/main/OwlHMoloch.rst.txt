OwlH and Moloch
===============


Configure Moloch
----------------

  * Install it on Master
  * Install in a remote server

Moloch in Master
----------------

  * Configure Moloch to read from owlh interface
  * Configure STAP on Master to collect socket and replay to owlh interface

Moloch in remote server
-----------------------

  * Configure NFS to publish a PCAP folder
  * Configure Master to connect to Moloch server PCAP folder
  * Configure OwlH Master Dispatcher to include Moloch PCAP folder in the pool
  * Configure STAP on Master to collect socket and write to PCAP