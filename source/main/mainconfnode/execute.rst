execute
=======

execute key 

.. code-block:: JSON

    {
        "execute":{
            "command":"sh",
            "check":"which",
            "param":"-c",
            "copy":"cp",
            "wget":"wget",
            "socatPID":"ps -aux | grep socat | grep OPENSSL-LISTEN:<PORT> | grep -v grep | awk '{print $2}'",
            "socNetExec":"-d OPENSSL-LISTEN:<PORT>,cipher=HIGH,method=TLS1.2,reuseaddr,pf=ip4,fork,cert=<CERT>,verify=0 SYSTEM:\"tcpreplay -t -i <IFACE> -\" &",
            "socNetFile":"-d OPENSSL-LISTEN:<PORT>,cipher=HIGH,method=TLS1.2,reuseaddr,pf=ip4,fork,cert=<CERT>,verify=0 SYSTEM:\"tcpdump -n -r - -s 0 -G 50 -W 100 -w <PCAP_PATH><PCAP_PREFIX>%d%m%Y%H%M%S.pcap <BPF>\" &",
            "NetSocFile":"-n -i <IFACE> -s 0 -w - <BPF> | <STAP> - OPENSSL:<COLLECTOR>:<PORT>,cert=<CERT>,verify=0,forever,retry=10,interval=5",
            "list":"ls -la",
            "suriPID":"ps -aux | grep suricata | <ID> grep -v grep | awk '{print $2}'",
            "openSSL":"ps -aux | grep OPENSSL:<COLLECTOR>:<PORT> | grep -v grep | awk '{print $2}'",
            "tcpdumpPID":"ps -aux | grep -v grep | grep tcpdump <TCPDUMP> | grep <IFACE> | grep '<BPF>' | awk '{print $2}'",
            "status":"status | grep running | awk '{print $5}'",
            "pidID":"ps -aux | grep <PID> | grep -v grep"
        }
    }


.. include:: /main/contact.rst