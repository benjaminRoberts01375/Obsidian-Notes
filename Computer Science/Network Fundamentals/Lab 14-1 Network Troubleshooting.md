#### Challenge 1 (about 5 minutes)
1. Attempt to ping router from laptops (good)
2. Attempt to ping laptops from router (good)
3. Attempt to have laptops ping each other (failed)
4. Check laptop default gateways
	1. Found Skiff laptop default gateway to be empty
	2. Have laptops ping each other
		1. After several pings, the laptops were able to successfully ping each other.
		2. ![[Lab 14 1.jpg]]

#### Challenge 2 (about 2 minutes)
1. Attempt to ping router from Foster laptop (known good)
2. Attempt to ping router from Skiff laptop (known bad)
3. Check difference between Foster and Skiff switches
	1. No difference found
4. Check difference between Foster and Skiff ports on router
	1. Skiff port had not been configured.
	2. Pull network deails from Skiff laptop.
	3. ![[Lab 14 2.jpg]]

#### Challenege 3 (About 7 minutes)
1. Attempt to have PCs 0-3 ping each other (good)
2. Attempt to have any PC ping router (all bad)
3. Investigate IP addresses
	1. Found cables from router were flipped
	2. ![[Lab 14 3.jpg]]

#### Challenge 4 (About 15 minutes)
1. Attempt to have PC0 and PC1 ping each other (good)
2. Have PC1 ping router1 (good)
3. Have PC1 ping router2 (good)
4. Have PC1 ping router3 (bad)
5. Have PC2 ping router3 (good)
6. Have router2 ping router3 (good)
7. Have router1 ping router3 (good)
8. Check static routes on all routers
	1. Found router3 was missing a route to the 192.168.10.0 network
	2. ![[Lab 14 4.jpg]]

#### Challenge 5 (About 10 minutes)
1. Found *technically* no problem since PC1 and PC2 can ping each other, though laptops are unable to at all
	1. Points to a subnetting problem
2. Check VLAN databases (good)
3. Check gigabit ports on switches are set to Trunk with correctly forwarded VLANs (good)
4. Check ports directly connected to laptop for correct VLAN (bad on second floor)
	1. Laptops can now ping each other
5. Ensure all devices can ping MultilayerSwitch0
6. Closed packet tracer and reopened
	1. Magically worked
	2. ![[Lab 14 5.jpg]]