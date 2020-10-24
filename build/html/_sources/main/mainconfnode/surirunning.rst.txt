suriRunning
===========

suriRunning key 

.. code-block:: JSON

    {
        "suriRunning":{
            "cmd": "ps -ef | grep suricata | grep -v grep | grep -v sudo | awk '{print $8 \" \" $2}' ",
            "param": "-c",
            "command": "bash"
        }
    }

.. include:: /main/contact.rst