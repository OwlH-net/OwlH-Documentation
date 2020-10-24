suricata
========

suricata key 

.. code-block:: JSON

    {
        "suricata":{
            "suricata":"suricata",
            "reload":"kill -USR2",
            "kill":"kill -9",
            "command":"bash",
            "param":"-c",
            "start":"systemctl start owlhsuricata",
            "stop":"systemctl stop owlhsuricata",
            "backup":"/var/run/suricata/",
            "pidfile":"pidfile.pid",
            "filter":"/etc/suricata/bpf/<ID>-filter.bpf",
            "fullpidfile":"/var/run/suricata/<ID>-pidfile.pid"
        }
    }

.. include:: /main/contact.rst