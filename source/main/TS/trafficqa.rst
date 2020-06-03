Traffic Quality
===============

Check your traffic to verify it is good enough. If there is no good traffic you won't see alerts as expected.



Is there any traffic? 
-----------------------

:: 

  # tcpdump -i ens192 -nn 

output should be verbose. 

* Can I see traffic that is not brocast or related to my interface? 

::

  # tcpdump -i ens192 -nn not arp and not net 224.0.0.0/8

output should be verbose.

* Try to filter out not relevant traffic, run previous command, find one or two ports that are no relevant and filter them

::

  # tcpdump -i ens192 -nn not arp and not net 224.0.0.0/8 and not port 22 and not port 443

Your output should show traffic in relevant ports. keep filtering adding ``and not port xxx`` as needed 

* Can I see local traffic only? 

Check if your interface can see remote traffic. This is supposing internal network is 172.16.0.0/16 and 10.0.0.0/8

:: 

  # tcpdump -i ens192 -nn not dst net 172.16.0.0/16
  # tcpdump -i ens192 -nn not dst net 172.16.0.0/16 and not dst net 10.0.0.0/8

you should see traffic with destination ips outside your network 

* bandwith, packet size, and other traffic statistics

Use a tool like iptraf-ng to review deteails about your traffic 

:: 

  # iptraf-ng -d eth0

   iptraf-ng 1.1.4
    ┌ Statistics for eth0 ─────────────────────────────────────────────────────────────────
    │               Total      Total    Incoming   Incoming    Outgoing   Outgoing       
    │             Packets      Bytes     Packets      Bytes     Packets      Bytes    
    │ Total:          200      33240         105       5532          95      27708     
    │ IPv4:           200      33240         105       5532          95      27708 
    │ IPv6:             0          0           0          0           0          0
    │ TCP:            200      33240         105       5532          95      27708
    │ UDP:              0          0           0          0           0          0
    │ ICMP:             0          0           0          0           0          0
    │ Other IP:         0          0           0          0           0          0
    │ Non-IP:           0          0           0          0           0          0
    │                                    │                                    
    │ Total rates:         36.46 kbps            Broadcast packets:            0
    │                         25 pps             Broadcast bytes:              0
    │                                                                            
    │ Incoming rates:       5.45 kbps    
    │                         12 pps     
    │                                            IP checksum errors:           0
    │ Outgoing rates:      31.00 kbps
    │                         12 pps











