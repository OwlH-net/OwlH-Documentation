OwlH and Zeek
=============

Integration Logical Diagram
---------------------------

.. image:: /img/broowlh.png

Components
^^^^^^^^^^

* OwlH Node - Zeek IDS and Wazuh Agent
* Wazuh Manger 
* Logstash Server
* Elastic and Kibana Server

Let's see what we need to modify on each component to be able to manage this Bro and Wazuh integration.


Configure - Zeek - OwlH Node
-----------------------------

This system will require Bro working of course, and Wazuh agent installed. OwlH instructions will help to configure both Bro and Wazuh agent.

Zeek Logs Output format to JSON
------------------------------

Option 1 - Modify ASCII writer output
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

you can load the json_logs.bro configuration that will tell ASCII writer to write output in JSON format.
You must include following line in your .bro configuration files. It can be /etc/bro/site/local.bro or you can follow our recomendation and write the configs in owlh.bro file (please, see below). 

This will modify output and will store just json output, you won't have ASCII output.

::

    @load tuning/json_logs.zeek


Zeek Event Enritchment to help Wazuh ruleset
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It is a good idea to help wazuh rules to do their job, to include a field that will identify what kind of log line we are analyzing. Bro output doesn't include that info per line by default, so we are going to help wazuh by including the field 'bro_engine' that will tell wazuh what kind of log is it. 

We are using redef function to include a custom field for each ::Info record of each Protocol. Here are just a few of them, we will include more by default in next releases. 

:: 

    redef record DNS::Info += {
        bro_engine:    string    &default="DNS"    &log;
    };
    redef record Conn::Info += {
        bro_engine:    string    &default="CONN"    &log;
    };
    redef record Weird::Info += {
        bro_engine:    string    &default="WEIRD"    &log;
    };
    redef record SSL::Info += {
        bro_engine:    string    &default="SSL"    &log;
    };
    redef record SSH::Info += {
        bro_engine:    string    &default="SSH"    &log;
    };

Loading Zeek customizations at Zeek start
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We include all OwlH customizations in OwlH_*.bro files, that helps to have a clear view of what OwlH does as well as we hope it will simplify configuration management. 

Under /etc/bro/site we will create two files 

* owlh.bro - Will include JSON call and @load for bro_engine field definition.
* owlh_types.bro - Will include all redef statments

You will only need to load OwlH.bro at the end of your local.bro file to include all these configurations

:: 

    @load /etc/bro/site/OwlH.bro

owlh.bro looks like: 

::
    
    @load tuning/json-logs.zeek
    @load owlh.zeek

and owlh.zeek:

:: 

    redef record DNS::Info += {
        bro_engine:    string    &default="DNS"    &log;
    };
    redef record Conn::Info += {
        bro_engine:    string    &default="CONN"    &log;
    };
    redef record Weird::Info += {
        bro_engine:    string    &default="WEIRD"    &log;
    };
    redef record SSL::Info += {
        bro_engine:    string    &default="SSL"    &log;
    };
    redef record SSH::Info += {
        bro_engine:    string    &default="SSH"    &log;
    };
 



Review your Kibana Dashboard
----------------------------

for integration with wazuh-elk you will need to verify that OwlH filebeat Module is loaded in Wazuh Manager servers and OwlH elasticsearch template and kibana dashboards are loaded.

:doc:`Configure and integrate with Wazuh-ELk<OwlH-elk>`


.. image:: /img/kibanabro.png


And that's all folks.


----