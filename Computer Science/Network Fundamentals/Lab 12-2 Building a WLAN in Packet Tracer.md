![[12-2 WLAN.pkt]]
#### Brief
- Setting up a **secure** wireless router and 3 laptops to connect to it for internet access.

#### Problems
- Nothing of note

#### Notes
1. Part 1: Following Part 1
	1. Setup Internet Connection type with a static LAN IP from the table
	2. Setup the Network Setup type with the LAN IP from the table
	3. Set the Network Mode to `Wireless-N Only`, and set the SSID to `CoolSSID`
	4. Disabled the broadcasting of the SSID
		1. Don't forget to save your settings
	5. Set the security to WPA2-Personal and configured a password
2. Part 2: Following Part 2
	1. Created a new Wireless Profile called "Wireless Profile" in Laptop1 > Desktop > PC Wireless
	2. After going through the setup, I accidentally clicked on "Connect" for the Default profile. I swapped over to the "Wireless Access" profile, and the Link Information was good after a small bit of time.
	3. Took a tiny screenshot for **Deliverable 1**
	4. Setup laptops 2 and 3 the same way as Laptop 1
3. Part 3: Following Part 3
	1. Connected the router with FA0/1 to the wireless router
	2. Connected the router with FA0/0 to the web server
	3. While the directions didn't say to, I setup the rest of the IPs
	4. I found an interesting issue of the router not being able to ping the wireless router, but the wireless router being able to ping the router. It doesn't seem to keep the laptops from pinging the webserver, though.

#### Tech Journal
-  https://drive.google.com/drive/folders/1_xQASZsI_NfIP3hmeVKnLXy41K6KIk-I

#### Deliverables:

| **Device**          | **Interface** | **IP Address**    | **Subnet Mask**   | **Default Gateway** |
| --------------- | --------- | ------------- | ------------- | --------------- |
| Router          | FA0/0     | 192.168.30.1  | 255.255.255.0 | N/A             |
| Router          | FA0/1     | 192.168.1.1   | 255.255.255.0 | N/A             |
| Laptop 1        | NIC       | DHCP          | 255.255.255.0 | 192.168.0.100   |
| Laptop 2        | NIC       | DHCP          | 255.255.255.0 | 192.168.0.100   |
| Laptop 3        | NIC       | DHCP          | 255.255.255.0 | 192.168.0.100   |
| Wireless Router | Internet  | 192.168.1.100 | 255.255.255.0 | 192.168.1.1     |
| Wireless Router | LAN       | 192.168.0.100 | 255.255.255.0 | 192.168.0.1     |
| Web Server      | FE0       | 192.168.30.15 | 255.255.255.0 | 192.168.30.1    |

1.  Configure a Wireless Router  
	1. Step 1: Configure the Internet connection type on the WR.  
		1. Click WR > GUI tab.  
		2. Set the Internet Connection type to Static IP.  
		3. Configure the Internet IP address according to the Addressing Table.  
	2. Step 2: Configure the network setup.  
		1. Scroll down to Network Setup. For the Router IP option, set the IP address to the Wireless Router’s LAN address and the subnet mask  
		2. Enable the DHCP server.  
		3. Scroll to the bottom of the page and click Save Settings.  
	3. Step 3: Configure wireless access and security.  
		1. At the top of the window, click Wireless. Set the Network Mode to Wireless-N Only and change the SSID to whatever you want to call your network.  
		2. Disable SSID Broadcast and click Save Settings.  
		3. Click the Wireless Security option.  
		4. Change the Security Mode from Disabled to WPA2 Personal.  
		5. Configure a passphrase.  
		6. Scroll to the bottom of the page and click Save Settings.
2. Part 2: Configure a Wireless Client
	1. Step 1: Configure Laptop1  for wireless connectivity. Because SSID broadcast is disabled, you must manually configure Laptop1 with the correct SSID and passphrase to establish a connection with the router.
		1. Click Laptop1 > Desktop > PC Wireless.
		2. Click the Profiles tab.
		3. Click New.
		4. Name the new profile Wireless Access. 
		5. On the next screen, click Advanced Setup. Leave on Infrastructure Mode.
			1. Then manually enter the SSID of your network on Wireless Network Name. Click Next. 
			2. Choose Obtain network settings automatically (DHCP) as the network settings, and then click Next. 
			3. On Wireless Security, choose WPA2-Personal as the method of encryption and click Next.
		7. Enter the passphrase and click Next. 
		8. Click Save and then click Connect to Network.
	2. Step 2: Verify Laptop1 wireless connectivity and IP addressing configuration.
		1. The Signal Strength and Link Quality indicators should show that you have a strong signal.
		2. Click More Information to see details of the connection including IP addressing information.  
		3. **SCREENSHOT #1** 
		- . **Deliverable 1:** Sorry it's so small, the window was tiny.![[Lab 12-2 1.jpg]]
		4. Close the PC Wireless configuration window.  
	3. Step 3: Configure Laptops 2 and 3 to connect to Wireless
4. Part 3: Connect to Wired Router and Web Server
	1. Step 1: Configure the Wired Router with the correct IP addresses per the Table.
		1. Connect the Wired Router to the Wireless Router using a crossover cable and correct ports.
		2. Connect the Wired Router to the Web Server using a crossover cable and the correct ports.  
	2. Step 2: Access Web server from the Laptops  
		1. Using the Web Browser on the laptops – connect to the Web Server  
		2. Show Laptop 2 & 3 connecting to Web Server.  
		3. **SCREENSHOT #2**  
		4. **Deliverable 2:**                                                  ![[Lab 12-2 2-3.jpg]]