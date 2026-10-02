# Windows Networking & DNS Troubleshooting

## Objective

Learn how to identify network settings, test connectivity, troubleshoot DNS, and trace network paths in Windows.

## Network Configuration

### `ipconfig`

**Purpose:** Displays the computer's basic IP configuration.  
**Result:** Reviewed the IPv4 address, subnet mask, and default gateway.

**IPv4 Address:** `10.0.2.15`  
**Default Gateway:** `10.0.2.2`

**What I Learned:** The IPv4 address identifies the VM on its network, while the default gateway is the device the VM uses to reach other networks.

## Connectivity Testing

### `ping 10.0.2.2`

**Purpose:** Tests whether the VM can communicate with its default gateway.  
**Result:** Received 4 replies with 0% packet loss.

**What I Learned:** A successful ping to the default gateway confirms that the computer can communicate with the local gateway.

### `ping 8.8.8.8`

**Purpose:** Tests internet connectivity using an IP address.  
**Result:** Received replies, confirming the VM could reach the internet.

### `ping google.com`

**Purpose:** Tests internet connectivity and DNS name resolution.  
**Result:** Received replies, confirming that the VM could reach the internet and resolve a domain name.

## DNS Troubleshooting

### `nslookup google.com`

**Purpose:** Queries DNS to determine which IP address is associated with a domain name.  
**Result:** The DNS server at `192.168.0.1` successfully resolved `google.com` to multiple IPv4 and IPv6 addresses.

### DNS Failure Simulation

**Test:** Queried `google.com` using `192.0.2.1` as a test DNS server.  
**Purpose:** Simulate what happens when a computer cannot communicate with a working DNS server.  
**Result:** The DNS request timed out when using the test DNS address. A normal `nslookup` using the configured DNS server successfully resolved `google.com`.

**What I Learned:** A DNS problem can prevent domain names from resolving even when the network connection itself is working.

## Network Path Analysis

### `tracert google.com`

**Purpose:** Shows the network path, or hops, that traffic takes to reach a destination.  
**Result:** The trace successfully reached `google.com`. Only one hop was displayed, likely because the VM is using VirtualBox NAT networking.

**What I Learned:** `tracert` can help identify where communication problems occur along the path between a computer and a remote destination.

## DNS Cache

### `ipconfig /displaydns`

**Purpose:** Displays DNS records currently stored in the Windows DNS cache.  
**Result:** Reviewed cached DNS records.

### `ipconfig /flushdns`

**Purpose:** Clears the Windows DNS resolver cache.  
**Result:** Successfully flushed the DNS Resolver Cache.

## What I Learned

- The IPv4 address identifies the VM on its network.
- The default gateway is used to reach other networks.
- `ping` can test basic connectivity.
- `nslookup` can verify DNS resolution.
- `tracert` shows the path traffic takes to a destination.
- `ipconfig /flushdns` clears the DNS resolver cache.
- DNS issues can prevent websites from resolving even when the network connection itself is working.
