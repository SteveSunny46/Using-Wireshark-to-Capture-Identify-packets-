# Using Wireshark to Capture and Identify Packets

## Scenario  
Your manager wants to detect certain TCP/IP network traffic on their server, specifically web traffic. 

## Goal 
• Look at web-based ethernet packets from a capture file you got. 

### Step 1
• We will need to modify the user account to append and add the current user to the Wireshark group, thus giving them packet capture capabilities for non-super users for security reasons. 

![image](https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/c4b36d41-43c3-465c-8b6b-287359db5aaf)

### Step 2
•	To begin, we will select the ethernet interface which typically begins with “en” and then start the Wireshark packet capture by pressing the blue shark fin on the top left.

![image](https://github.com/SteveSunny46/Using-Wireshark-to-Capture-Identify-packets-/assets/171859383/add21fc2-ac8c-4c62-9610-5ef1629d9b51)


### Step 3
•	Next, we'll capture packets to demonstrate the exchange when connecting to the secure website duckduckgo.com (HTTPS), and then use a display filter to isolate HTTPS traffic on port 443.

•	We'll observe a TCP 3-way handshake: SYN from the device to the website's IP, SYN-ACK from the website to the device, and ACK from the device to the website.

•	Further below, we'll see the "Client Hello," indicating the preferred encryption method, followed by the "Server Hello," confirming TLS encryption parameters in the TLS handshake. 





