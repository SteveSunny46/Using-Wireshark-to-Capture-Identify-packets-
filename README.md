# Using Wireshark to Capture and Identify Packets

## Scenario  
Your manager wants to detect certain TCP/IP network traffic on their server, specifically web traffic. 

## Goal 
• Look at web-based ethernet packets from a capture file you got. 

### Step 1: Configure User Account for Packet Capture
• We will need to modify the user account to append and add the current user to the Wireshark group, thus giving them packet capture capabilities for non-super users for security reasons. 

<img width ="503" alt="1" src="https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/6bbc09f6-8221-42b6-b3a5-40675a37e83e">

### Step 2: Start Packet Capture on Ethernet Interface
•	To begin, we will select the ethernet interface which typically begins with “en” and then start the Wireshark packet capture by pressing the blue shark fin on the top left.

<img width="503" alt="1" src="https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/2234b474-397b-4570-a7c8-3817927fa61c">


### Step 3: Capture and Analyze HTTPS Traffic
•	Next, we'll capture packets to demonstrate the exchange when connecting to the secure website duckduckgo.com (HTTPS), and then use a display filter to isolate HTTPS traffic on port 443.

•	We'll observe a TCP 3-way handshake: SYN from the device to the website's IP, SYN-ACK from the website to the device, and ACK from the device to the website.

•	Further below, we'll see the "Client Hello", which is from the user device to the web server which indicates the preferred encryption method, followed by the "Server Hello", this is from the server to the user confirming TLS encryption parameters in the TLS handshake. 

<img width="503" alt="1" src="https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/f981635a-700d-4c6e-a440-b9a44a26f355">

### Step 4: Filter and Identify TLS Handshake Packets
•	In this example, we've captured Ethernet traffic for Google.com 
(note: Google.com may have a different IP address as they tend to use different IP addresses for different users). 

•	By filtering with tls.handshake.type == 1, we can locate all the "Client Hello" messages in the TLS handshake and identify the Google IP. 

•	Similarly, substituting the number 1 with 2 allows us to find the "Server Hello" step in the TLS handshake.

<img width="468" alt="1" src="https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/01110f80-e579-431e-adf1-97ca2f794f1d">

### Step 5: Filter Packets by IP Address
•	To target specific IP addresses, we can use ip.addr == 172.253.122.106. For finer control, "ip.src == ..." can be used to find packets that came from the specified source IP address or "ip.dst == ..." to find packets where its destination was the specified IP address. 

<img width="444" alt="1" src="https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/218b1859-82c4-46d1-b763-b5fbf402d5e5">

### Step 6: Exclude Specific IP from Traffic Analysis
•	We can also find specific web traffic that occurred while excluding a specific IP. 

•	In this example we are displaying all port 443 and port 80 traffic while excluding the Google IP we received. This gives us a finer look at the web traffic packets to analyze while avoiding the extra fluff of IP addresses we don't want to focus on.  

<img width="390" alt="1" src="https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/adef3a50-98c4-4902-a9bf-cb870f4029bd">




