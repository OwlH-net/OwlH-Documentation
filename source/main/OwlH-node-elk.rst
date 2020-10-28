
Sync with ELK 7.x
=================

.. warning::

    Be sure you are running ELK (elasticsearch, filebeat and kibana) with version >7.3.2

.. include:: keepincontact.rst

This process will allow you to connect your OwlH environment directly to ELK. 

You will do:

  * install filebeat on OwlH Nodes
  * install OwlH-Filebeat module 
  * import OwlH-Kibana objects in Kibana
  * load OwlH template in Elasticsearch
  * modify Filebeat main configuration to include OwlH module


.. note:: 
  Please, check URLs and paths to ensure you use the right commands and that you adapt command lines as needed. 


Download files and prepare
^^^^^^^^^^^^^^^^^^^^^^^^^^

::
    
    # cd /tmp
    # mkdir /tmp/owlhfilebeat
    # cd /tmp/owlhfilebeat
    # wget repo.owlh.net/fbit/owlh-module.tar.gz
    # tar -C /tmp/owlhfilebeat -xf owlh-module.tar.gz


Install OwlH module
-------------------

::

    # tar -C /usr/share/filebeat/module/ -xf /tmp/owlhfilebeat/owlh-filebeat-7.9.x.tar.gz


Modify filebeat
^^^^^^^^^^^^^^^

Modify Filebeat configuration
-----------------------------

::

    # cp /tmp/owlhfilebeat/filebeat.yml /etc/filebeat/filebeat.yml 

.. attention:: 
    be sure to update properly your filebeat.yml file to point to your elasticsearch server.



Restart Filebeat
----------------

You should be done. check your kibana to see the OwlH dashboards in dashboards section, and indices in discovery section.

::

    Restart Filebeat

    # systemctl restart filebeat 

    Check Filebeat output

    # journalctl -f -u filebeat

    From your web browser, check kibana->discovery for owlh indices.
