API service configuration files
===============================

Node configuration
------------------

::

  appname = OwlHnode
  runmode = dev
  autorender = false
  copyrequestbody = true
  EnableDocs = true
  ListenTCP4 = true
  EnableHTTP = false
  EnableHTTPS = true
  HTTPSAddr = "0.0.0.0"
  HTTPSPort = 50002
  HTTPSCertFile = "conf/certs/ca.crt"
  HTTPSKeyFile = "conf/certs/ca.key"
  EnableDocs = true


Master configuration
--------------------

::

  appname = OwlHmaster
  runmode = dev
  autorender = false
  copyrequestbody = true
  EnableDocs = true
  ListenTCP4 = true
  EnableHTTP = false
  EnableHTTPS = true
  HTTPSAddr = "0.0.0.0"
  HTTPSPort = 50001
  HTTPSCertFile = "conf/certs/ca.crt"
  HTTPSKeyFile = "conf/certs/ca.key"
  EnableDocs = true
