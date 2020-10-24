zeek
====

zeek key 

.. code-block:: JSON

    {
        "zeek":{
            "zeekctl":"/usr/local/zeek/bin/zeekctl",
            "nodeconfig":"/usr/local/zeek/etc/node.cfg",
            "networkconfig":"/usr/local/zeek/etc/networks.cfg",
            "zeekctlconfig":"/usr/local/zeek/etc/zeekctl.cfg",
            "zeekconfig":"/usr/local/zeek/etc/",
            "zeekpath":"/usr/local/zeek",
            "status":"/usr/local/zeek/bin/zeekctl status | grep standalone | awk '{print $1 \" \" $4}'",
            "currentstatus":"status",
            "stop":"stop",
            "start":"start",
            "deploy":"deploy"
        }
    }

.. include:: /main/contact.rst