stap
====

stap key 

.. code-block:: JSON

    {
        "stap":{
            "in_queue":"/usr/share/owlh/in_queue/",
            "out_queue":"/usr/share/owlh/out_queue/",
            "interface":"owlh",
            "keepPCAP":"false",
            "plugin":"/usr/bin/socat",
            "tcpdum":"/usr/sbin/tcpdump",
            "tcpreplay":"tcpreplay -i <IFACE> -t -l 1 <NAME>",
            "checkTCPDUMP":"tcpdump",
            "checkTCPREPLAY":"tcpreplay",
            "checkSOCAT":"socat"
        }
    }

.. include:: /main/contact.rst