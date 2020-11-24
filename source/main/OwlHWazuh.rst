Integration with Wazuh-ELK
==========================

if you want to send OwlH output including Suricata and Zeek alerts and logs to Wazuh-ELK

This will help to integrate your NIDS alerts and output into Wazuh world. this is a one-way integration process.

Main steps
^^^^^^^^^^

* Install and register your Wazuh Agent in the OwlH Node
* Enable OwlH Node Analyzer
* Add OwlH filebeat Module in your OwlH Manager
* Import OwlH dashboards in your ELK Kibana

----


Install Wazuh Agent
-------------------

.. tabs::


  .. group-tab:: Yum


    .. include:: /main/OwlHWazuhAgentCentos


  .. group-tab:: APT


    .. include:: OwlHWazuhAgentDebian

    
Register your Wazuh Agent with your Wazuh Manager, and modify the ossec.conf file to point to it as needed. Please follow your Wazuh deployment process to run this step or refer to Wazuh's documentation.


Configure Wazuh Agent to read OwlH output
-----------------------------------------

We need to tell our Wazuh Agent to read the OwlH Output where NIDS alerts and logs are stored. The file is created by the OwlH Analyzer and by default is /var/owlh/alerts.json. Be sure Analyzer is configured and working

You can configure this from User Interface:

:: 

  UI -> nodes -> search your node -> node services configuration -> Wazuh -> add file
  include the alerts.json path where Analyzer is storing events 
  save and reload Wazuh 

You can verify if there are new lines in the alerts.json file, UI will show current size and you can refresh it. also, you can verify ossec.log file to check if there are any errors. 

To monitor ossec.log file: 

:: 

  UI -> nodes -> search your node -> monitor node -> add file
  include your ossec.log file -> /var/ossec/logs/ossec.log
  review the latest 10, 50 or 100 lines.

Wazuh manager and ELK configuration
-----------------------------------

Now you need to ensure that your Wazuh Manager is configured to manage OwlH output and is able to send to ELK properly. Also you may need to import in your ELK the default OwlH Dashboards

Follow the instructions here. 

* :doc:`ELK integration <OwlH-elk>`

