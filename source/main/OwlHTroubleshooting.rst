Troubleshooting
====================

.. warning::

    work in progress... 

.. include:: /main/missing.rst


.. image:: /img/trb01.png

OwlH Node 
---------

:doc:`Suricata doesn't create alerts<TS/suricata>`


OwlH Master
-----------

OwlH UI
-------

OwlH Dashboards on Kibana
-------------------------

Can't see any alert on owlh-alert dashboard

* Check search owlh alert (discover -> open) is using wazuh-alerts-3.x, wazuh-alerts-4.x or wazuh-alerts-* depending on your Wazuh version. if you are running wazuh 3.x use wazuh-alerts-3.x. if running wazuh 4.x choose wazuh-alerts-*. Save, you should see now events in discovery, if any then your dashboard should work now. 

* reload wazuh index pattern

