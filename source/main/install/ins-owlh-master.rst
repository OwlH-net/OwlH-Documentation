Install OwlH Master
===================

.. include:: /main/OwlHInstallerDownload.rst


.. note:: 
    Right now, our target is "owlhui" and "owlhmaster", our action is "install"

:: 

  {
  "versionfile":"current.version",
  "masterbinpath":"/root/workspace/src/owlhmaster/",
  "masterconfpath":"/root/workspace/src/owlhmaster/conf/",
  "mastertarfile":"owlhmaster.tar.gz",
  "nodebinpath":"/root/workspace/src/owlhnode/",
  "nodeconfpath":"/root/workspace/src/owlhnode/conf/",
  "nodetarfile":"owlhnode.tar.gz",
  "uipath":"/var/www/owlh/",
  "uiconfpath":"/var/www/owlh/conf/",
  "uitarfile":"owlhui.tar.gz",
  "tmpfolder":"/tmp/",
  "action": "install",      <===
  "repourl":"http://repo.owlh.net/current-centos/",    <=== Be sure to set right repo
  "target": [
      "owlhmaster",         <===
      "owlhui"              <===
  ],
  "masterfiles":[
      "main.conf",
      "app.conf"
  ],
  "nodefiles":[
      "main.conf",
      "stap-defaults.json",
      "app.conf"
  ],
  "uifiles":[
      "ui.conf"
  ],
  "masterdb":[
      "group.db",
      "node.db",
      "ruleset.db",
      "plugins.db"
  ],
  "nodedb":[
      "plugins.db",
      "servers.db"
  ]
  }


.. attention::
    you can change your installation paths as needed. Changing default paths may need further paths change for some configurations like service init files. If you are not familiar with it, keep defaults until it is really needed or ask for help.


Verify your libpcap library is installed. 
`````````````````````````````````````````````````````

::

    CentOS: 
        # yum -y install libpcap0.8
    Debian/Ubuntu: 
        # apt-cache -y install libpcap

run OwlH Installer to install OwlH UI and OwlH Master
`````````````````````````````````````````````````````

:: 

    # cd /tmp/owlhinstaller
    # ./owlhinstaller

Configure your Master and UI 

::

    if CentOs:
        # wget http://repo.owlh.net/current-centos/services/owlhui-httpd.sh
        # bash owlhui-httpd.sh
    if Debian/Ubuntu:
        # wget http://repo.owlh.net/current-debian/services/owlhui-httpd.sh
        # bash owlhui-httpd.sh
    both OS:
        # cp /usr/local/owlh/src/owlhmaster/conf/service/owlhmaster.service /etc/systemd/system
        # systemctl daemon-reload
        # systemctl start owlhmaster.service



Check if your OwlH Master is running  
````````````````````````````````````

:: 

    check owlhmaster logs 
    # tail -f /var/log/owlh/owlhmaster-api.log

    check owlhmaster process is running
    # systemctl status owlhmaster.service
    # ps -ef | grep owlhmaster

    check if owlhmaster service port is listening
    # netstat -nputa | grep 50001


Modify your OwlH Installer configuration to keep your system uptodate
`````````````````````````````````````````````````````````````````````


.. note:: 
    Right now, our target is "owlhmaster", our action is "update". 

modify your config.json file to set action as "update".

:: 

  ...
  "tmpfolder":"/tmp/",
  "action": "update",      <===
  "repourl":"http://repo.owlh.net/current-centos/",  <=== Repo url may vary
  "target": [
      "owlhmaster"            <===
  ],
  ...

You can add owlhinstaller to your crontab for an automatic update of your platform. following lines will move OwlH installer and create cron job. Please change as needed. 

.. note:: While this is recommended, it is not mandatory. you can run your OwlH Installer manually as per your needs

:: 

    # mkdir /usr/local/owlh/src/owlhinstaller
    # cp /tmp/owlhinstaller/* /usr/local/owlh/src/owlhinstaller/
    # (crontab -l ; echo "0 0 * * * /usr/local/owlh/src/owlhinstaller/owlhinstaller ") | crontab -

