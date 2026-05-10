# Packets & Frames

Theory 

Frame vs Packet — the critical difference:

Frame: Layer 2 (Data Link) - MAC addresses + a packet inside	Only on your local LAN

Packet:	Layer 3 (Network) - IP addresses + data	Can cross the internet

Analogy:

- A packet is like a letter with a destination address (IP)

- A frame is like an envelope with the next hop's street address (MAC)

Your router opens the envelope, reads the letter, and re‑wraps it for the next hop

 ETHERNET FRAME 

  - MAC src (your device)
  - MAC dst (your router)
  
 IP PACKET 
    
   -  IP src (your IP)
   -  IP dst (google.com)
    
 DATA / PAYLOAD 
    
   -  Could be a password, command, or exploit


Why this matters:

1. ARP spoofing	: Forge MAC addresses in frames	(Layer 2)
2. IP spoofing :Forge source IP in packets	(Layer 3)


Key rule:

- Frames stay on your LAN. Packets cross the internet.

You can't send a frame to Tokyo : only to your local router, which strips it and forwards the packet.

---

## Quick Quiz 

---

1. If you send a ping to 8.8.8.8 (Google DNS), does your computer create a frame, a packet, or both?

Actually both. Ping creates a packet (IP) inside a frame (Ethernet). Without the frame, the packet never leaves your NIC.

2. When the ping reaches your router, does the router forward the same frame or a new frame to the next hop?

New frame : This is because router strips old MAC, builds new frame for next hop

3.  True or False: A packet contains MAC addresses inside it.

False : MAC is Layer 2

4. Why would a hacker craft a custom frame instead of a normal packet?

Frames stay on LAN :  ARP spoofing (Layer 2) only works locally

---

### Hands‑on Task 

You need Wireshark 

Download from wireshark.org

Install with default settings

Then do this:

- Open Wireshark and select your network interface (Wi-Fi or Ethernet)

- Start capture (fin button)

- Open your browser and go to http://neverssl.com (http site)

- Stop capture after 5 seconds

- Find a frame + packet:

- In Wireshark, click on any line

- Look at the bottom panel — expand "Ethernet II" (that's your frame — MAC addresses)

- Expand "Internet Protocol" (that's your packet — IP addresses)

Questions for you:

1. What's the source MAC address in the frame?

![Networkingimages](Networkingimages/image6.png)


2. What's the destination IP address in the packet?

![Networkingimages](Networkingimages/image7.png)


3. Do they match your arp -a results from earlier? If not, why?