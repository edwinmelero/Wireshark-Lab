# Wireshark

In this scenario, consider that you are working for a security solutions provider. You are performing threat hunting on existing network packet captures recorded on your customers' systems. You must identify and classify any attacks suggested by indicators in the packet captures and identify what you can do to prevent such attacks in the future.
<br>
<br>
1. From here we see on the top pane, packet capture 1 the source and destination IP address is 10.39.5.6
2. The information we see on the middle pane is the field-by-field interpretation which shows the destination port of 443 which is HTTPS. 
3. We can also see the SYN flag set for this packet. 

![image](https://github.com/itzyezz/Wireshark/assets/105263523/f2a7eab2-7df5-4d39-83f2-e10f959802e7)
<br>
<br>
<br>
From the menu, I selected **Analyze > Expert Information**.
<br>
<br>
This report shows a list of anomalies discovered in the capture. While it is always useful to have a baseline of normal traffic for comparison, the number of resets in this capture is very high. There are also a lot of connection requests (chats) for a wide range of ports.

![image](https://github.com/itzyezz/Wireshark/assets/105263523/f1b71d1a-1dd2-4fa0-99bc-3b31352e9f05)
<br>
<br>
<br>
From the menu, I selected **Statistics > Protocol Hierarchy**.
<br>
<br>
This shows the mix of protocols that were captured. In this case, the traffic is almost exclusively TCP, with some ICMP. No higher-level protocols are observed. This could have been a feature of the traffic or a capture filter could have been applied.

![image](https://github.com/itzyezz/Wireshark/assets/105263523/a8ebd6cb-39ea-43c7-af72-b887c63aeb44)
<br>
<br>
<br>
From the menu, I selected **Statistics > Capture File Properties**.
<br>
<br>
This shows the details of the host and interface from which the capture was recorded. Note that no capture filter was applied.

![image](https://github.com/itzyezz/Wireshark/assets/105263523/2f348ab6-8ffa-45d9-afb8-bac85f66881a)
<br>
<br>
<br>
From the menu, I select **Statistics > Conversations**.
<br>
<br>
1. Note there are many one-packet sessions
2. Note the various destination port (port B) numbers.
3. Note the extremely short duration of each conversation
4. Note the small size of each packet.

![image](https://github.com/itzyezz/Wireshark/assets/105263523/e284e0c8-9fb2-4717-9244-55c480b5eb44)
<br>
<br>
<br>
I right-click Packet 1 and selected **Follow > TCP Stream** from the menu to look at just one session.

![image](https://github.com/itzyezz/Wireshark/assets/105263523/4aa366e8-9193-4f92-8487-190d88c7e51e)
<br>
<br>
<br>
If there were data in the session, you would see it, but there isn't any in this case.

![image](https://github.com/itzyezz/Wireshark/assets/105263523/303daee9-351d-4a32-94d2-baa07f9939f0)
<br>
<br>
<br>
After closing the previous window, note that a display filter has now been applied, limiting the view to the three packets in that first stream.
<br>
<br>
Looking at the flags of these 3 packets we can determine the attacker started a session but then reset it after getting the server response. Note that the **RST** is sent by **10.39.5.6**

![image](https://github.com/itzyezz/Wireshark/assets/105263523/468e4b3a-2dd8-4c4d-a104-50f13d9f73b0)
<br>
<br>
<br>
Selecting packet 42. Looking at the summary of packets 42 and 43, we can see the attacker tried to connect using the telnet protocol on **port 23** but was refused by the server. Note that the **RST** was sent by the server **10.39.5.2**

![image](https://github.com/itzyezz/Wireshark/assets/105263523/343f9727-3b98-4c89-abc5-c33d06561cb5)
<br>
<br>
<br>

From the information we gathered, We can determine the attacker was trying to discover which port numbers were open and which were not. In other words, a port scan. The attacker can then proceed after learning this information, what services are running on open ports, and try to attack those services. 







