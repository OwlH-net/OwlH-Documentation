loadDataWazuhRunning
====================

loadDataWazuhRunning key 

.. code-block:: JSON

    {
        "loadDataWazuhRunning":{
            "cmd": "/var/ossec/bin/ossec-control status | grep logcollector",
            "param": "-c",
            "command": "bash"
        }
    }


.. include:: /main/contact.rst