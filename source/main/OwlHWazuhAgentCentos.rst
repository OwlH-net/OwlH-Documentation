
1. Import the GPG key:

.. code-block:: console

  # rpm --import https://packages.wazuh.com/key/GPG-KEY-WAZUH


2. Add Wazuh repository

.. code-block:: console

    # cat > /etc/yum.repos.d/wazuh.repo << EOF
    [wazuh]
    gpgcheck=1
    gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
    enabled=1
    name=EL-$releasever - Wazuh
    baseurl=https://packages.wazuh.com/4.x/yum/
    protect=1
    EOF

3. Install wazuh - agent 

.. note:: 

  You can use your own wazuh-agent installation and registration procedure. 

.. code-block:: console

  # yum -y install wazuh-agent

  or 

  # WAZUH_MANAGER="10.0.0.2" yum install wazuh-agent

4. Enable and start your Wazuh-agent 

.. code-block:: console

  # systemctl daemon-reload
  # systemctl enable wazuh-agent
  # systemctl start wazuh-agent