1. Install the GPG key:

.. code-block:: console

    # curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | apt-key add -

2. Add the repository:

.. code-block:: console

    # echo "deb https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list

3. Update the package information:

.. code-block:: console

    # apt-get update

4. Install wazuh-agent

.. code-block:: console 

    # apt-get install wazuh-agent

    or 

    # WAZUH_MANAGER="10.0.0.2" apt-get install wazuh-agent

5. Enable and start your Wazuh-agent 

.. code-block:: console

  # systemctl daemon-reload
  # systemctl enable wazuh-agent
  # systemctl start wazuh-agent