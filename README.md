# Detecting-DOS-attack-using-Snort-as-Network-Intrusion-Detection-System-NIDS-in-a-virtual-Lab
Developed a virtual lab to simulate and detect DoS attacks using Snort as a Network Intrusion Detection System (NIDS). Configured custom rules to identify ICMP and SYN flood attacks generated from an attacker machine, and analyzed real-time alerts through the command-line interface.

## Disclaimer
This project was conducted strictly in a controlled lab environment for educational purposes only.

## Lab Environment
- Attacker Machine: Kali Linux
- Target Machine: Metasploitable2
- Tool: Snort
- Network Type: Isolated / Host-only Network
  
## Analysis flow
<b>1. Lab setup</b>
<br>
This image shows the network setup used in a virtual penetration testing lab. On the left side, a Kali Linux machine is configured as the attacker with IP address 192.168.56.102, verified using the ifconfig command. On the right side, a Metasploitable2 machine is used as the target system with IP address 192.168.56.103, confirmed using the ip a command.

Both machines are connected within the same virtual network (192.168.56.0/24), allowing direct communication between attacker and target. This setup enables the simulation of various attack scenarios such as DoS (ICMP/SYN flood), vulnerability scanning, and intrusion detection testing using tools like Snort. The environment is isolated, making it safe for cybersecurity experimentation and learning purposes.

<b>2. Ping Flood from Attacker </b><br>
This image demonstrates an ICMP flood attack initiated from the Kali Linux attacker machine targeting the Metasploitable2 system at IP address 192.168.56.103 using the ping -f command. The output shows a high volume of packets being transmitted in a short period of time, with 6412 packets sent and received, indicating no packet loss during the attack. This type of traffic simulates a Denial-of-Service (DoS) scenario by overwhelming the target with continuous ICMP requests, which can be used to test the effectiveness of intrusion detection systems such as Snort in identifying abnormal network behavior.

<b>3. ICMP Flood Detection </b><br>
This image shows Snort successfully detecting an ICMP flood attack within the virtual lab environment. The alerts indicate repeated ICMP traffic originating from the attacker machine (192.168.56.102) targeting the Metasploitable2 system (192.168.56.103). Each alert is triggered based on a custom detection rule that identifies a high number of ICMP packets within a short time frame, classifying the activity as a potential Denial-of-Service (DoS) attack. This demonstrates how Snort, as a Network Intrusion Detection System (NIDS), can monitor network traffic in real time and generate alerts for abnormal behavior, helping identify and respond to potential threats.

<b>4. SYN Flood from attacker </b><br>
This image demonstrates a SYN flood attack launched from the Kali Linux attacker machine targeting the Metasploitable2 system on port 80 using the hping3 tool. The command sends a massive number of TCP SYN packets in flood mode, as shown by the high number of transmitted packets (998,989) with no responses received from the target, resulting in 100% packet loss. This behavior simulates a Denial-of-Service (DoS) attack by overwhelming the target server with connection requests, preventing it from responding to legitimate traffic. The scenario is used to evaluate the effectiveness of intrusion detection mechanisms such as Snort in identifying SYN flood attacks.

<b>5. SYN Flood detection</b><br>
This image shows Snort detecting a SYN flood attack targeting the Metasploitable2 system on port 80. The alerts indicate repeated TCP connection attempts originating from the attacker machine (192.168.56.102) using different source ports, which is characteristic of a SYN flood attack. Each alert is triggered by a custom Snort rule that identifies excessive SYN packets within a short time frame and classifies the activity as a potential Denial-of-Service (DoS) attack. This demonstrates Snort’s capability as a Network Intrusion Detection System (NIDS) to monitor TCP traffic in real time and generate alerts for abnormal connection patterns.
