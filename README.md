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
