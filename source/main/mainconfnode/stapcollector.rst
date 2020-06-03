stapCollector
===========

stapCollector key 

.. code-block:: JSON

    {
        "stapCollector":{
            "start":"systemctl start owlh-stapcollector",
            "stop":"systemctl stop owlh-stapcollector",
            "status":"netstat -nputa | grep 50010",
            "param":"-c",
            "command":"bash"
        }
    }


.. include:: /main/contact.rst