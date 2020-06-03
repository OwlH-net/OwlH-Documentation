service
=======

service key 

.. code-block:: JSON

    {
        "service":{
            "file":"owlhnode.service",
            "origPath":"conf/service/",
            "dstPath":"/etc/systemd/system/",
            "reload":"systemctl daemon-reload",
            "enable":"systemctl enable owlhnode"
        }
    }


.. include:: /main/contact.rst