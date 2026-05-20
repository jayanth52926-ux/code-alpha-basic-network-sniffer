# basic-network-sniffer
This is a simple Python network sniffer built for learning how packets flow through a network.




***What it does***

Captures live network traffic on a chosen interface
Displays:
source IP
destination IP
protocol type (TCP / UDP / ICMP / other)
transport details (TCP/UDP ports, ICMP type/code)
payload summary (ASCII + hex snippet)





_**How it captures packets**_

The script supports two capture modes:

scapy mode
Uses scapy if installed
Easier packet parsing and protocol detection
Enabled automatically unless --no-scapy is given
Raw socket fallback
Uses Linux AF_PACKET raw socket
Parses Ethernet, IPv4, and basic transport headers manually
Works when scapy is unavailable, but only on Linux.










What the code contains

1. format_payload(...)
2. converts packet payload bytes into readable ASCII + hex
3. describe_scapy_packet(packet)
4. extracts IP/TCP/UDP/ICMP info from a scapy packet
5. scapy_capture(...)
6. calls scapy.sniff(...) and prints each packet
7. parse_ethernet_header(...)
8. reads Ethernet header fields from raw data
9. parse_ipv4_header(...)
10. reads IPv4 header fields and payload offset
11. parse_transport_header(...)
12. reads TCP/UDP/ICMP headers from the IPv4 payload
13. raw_socket_capture(...)
14. receives raw packets from a Linux interface and prints parsed info

# How to run

How to run it


_python3 sniffer.py -i <interface>_
Optional flags:

-c N — capture N packets then stop
--no-scapy — force raw socket capture
What you learn from it

1. Basic packet structure:
      Ethernet header → IPv4 header → TCP/UDP/ICMP payload
2. How to inspect packet fields in Python
3. The difference between high-level libraries (scapy) and manual raw socket parsing
4. How network traffic flows across interfaces


# Important notes

1. Raw socket mode requires root privileges on Linux
2. scapy must be installed in the same Python environment used to run the script
wlan0.
3. Other names are interface names, and must exist on the system
