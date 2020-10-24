loadDataZeekRunning
===================

loadDataZeekRunning key 

.. code-block:: JSON

    {
        "loadDataZeekRunning":{
            "cmd":"/usr/local/zeek/bin/zeekctl status | grep standalone | awk '{print $1 \" \" $4}'",
            "param":"-c",
            "command":"bash"
        }
    }

.. include:: /main/contact.rst