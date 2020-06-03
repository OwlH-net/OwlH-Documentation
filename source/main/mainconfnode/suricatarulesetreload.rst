suricataRulesetReload
=====================

suricataRulesetReload key 

.. code-block:: JSON

    {
        "SuricataRulesetReload":{
            "suricatasc": "/usr/bin/suricatasc",
            "param": "-c",
            "reload": "reload-rules",
            "socket": "/var/run/suricata/suricata-command.socket"
        }
    }

.. include:: /main/contact.rst