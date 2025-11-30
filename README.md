# VIEW-CAPTURED-TRAFFIC-IN-WIRESHARK-ARP-
This project demonstrates how to capture, inspect, and analyze ARP (Address Resolution Protocol) traffic using Wireshark, as well as how to view local ARP cache entries on a PC. The lab walks through capturing ARP requests/replies, analyzing data at multiple protocol layers, and understanding how ARP functions within a TCP/IP network.

📌 Objectives
Part 1: Download and Install Wireshark

Install the Wireshark packet analyzer.

Part 2: Capture and Analyze ARP Data in Wireshark

Start and stop ARP-related packet captures.

Filter traffic to display ARP PDUs only.

Locate IPv4 and MAC information in captured frames.

Examine the structure and content of ARP request and response messages.

Part 3: View ARP Cache Entries on the PC

Access the Windows Command Prompt.

Use arp commands to inspect the local ARP table.

🧠 Background / Scenario

ARP (Address Resolution Protocol) maps a device’s IPv4 address (Layer 3) to its MAC address (Layer 2).
When a device wants to send an Ethernet frame, it must know the destination’s MAC address. If it doesn’t, it sends a broadcast ARP Request, and the device with the matching IPv4 address responds with an ARP Reply. These responses are stored in the ARP cache, allowing faster communication without repeated broadcasts.

Wireshark is a packet-sniffing tool used to capture and analyze PDUs (protocol data units). In this lab, Wireshark helps visualize ARP exchanges happening on a LAN, showing how devices discover each other's Layer 2 addresses.

🛠️ Lab Tasks
Part 1: Install Wireshark

Download Wireshark from its official site.

Follow installation prompts (WinPcap/Npcap installation recommended).

Part 2:  Capture & Analyze Local ARP Traffic
🔎 Step 1: Retrieve PC Interface Addresses

Open Command Prompt and run:

ipconfig /all

![image](https://github.com/heis-cyb3rski/VIEW-CAPTURED-TRAFFIC-IN-WIRESHARK-ARP-/blob/23e403d45c2d0ebf072889026aed61f68ccda0e5/ipconfig%20cmd%20.png)

Identify the active network adapter.

Record:

IPv4 Address

MAC Address (Physical Address)

🐬 Step 2: Start Wireshark and Capture ARP Packets

Launch Wireshark.

Select the network interface identified earlier.

Apply ARP filter:

arp


Start packet capture (shark fin icon).

In Command Prompt, ping the default gateway:

ping <default-gateway-ip>


Stop capture (red square icon).

📂 Step 3: Analyze Captured ARP Frames

Wireshark displays captured data in three panes:

Top: Summary of captured packets.

Middle: Layer-by-layer packet details.

Bottom: Raw data (hex and decimal).

Actions:

Select an ARP frame where:

Your MAC = Source

Destination = Broadcast

Expand Ethernet II → view Source & Destination MACs.

Expand Address Resolution Protocol (Request) → inspect ARP fields.

📨 Step 4: Identify Matching ARP Response

Use the Target IPv4 Address from the ARP Request.

Locate the corresponding ARP Reply in the capture list.

Inspect:

Sender MAC / IPv4

Target MAC / IPv4

Compare Request → Response to understand ARP resolution.

📄 Part 3: View Local ARP Cache

Open Command Prompt.

Use:

arp -a


Review:

Cached IPv4 addresses

Corresponding MAC addresses

Entry types (dynamic/static)

✔️ What I Learnt in this Lab

How ARP resolves Layer 3 addresses to Layer 2.

How Wireshark captures and decodes ARP traffic.

How to interpret Ethernet and ARP headers.

How to manually inspect the ARP cache on a PC.

