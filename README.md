# DNS Spoofer

This project demonstrates a DNS spoofing attack, which redirects a target's DNS queries for a specific domain to a malicious server. For this example, we will redirect `www.bing.com` to an Apache2 web server hosted on `ip`.

---

## How It Works

1. **Becoming the MITM**  
   To intercept and manipulate network traffic, you must first position yourself as the **Man-in-the-Middle (MITM)**. This is achieved using an ARP spoofer (you can use the `arp_spoofer` script).

2. **Enabling Packet Forwarding**  
   To allow intercepted packets to flow through your computer, run the following commands:
   ```bash
   sudo nft add chain ip filter forward '{ type filter hook forward priority 0 ; }'
   sudo nft add rule ip filter forward counter queue num 0
3. **Starting Apache2**
The DNS spoofing attack will redirect traffic to a web server. Here, we use Apache2:

```bash
sudo service apache2 start
```
4. **Running the DNS Spoofer**
The DNS spoofer intercepts DNS queries and modifies responses, directing www.bing.com to my webserver

This DNS Spoofer script enables users to intercept and manipulate DNS queries within a network, redirecting specific domain requests to a malicious server of choice. By positioning the attacker as a Man-in-the-Middle (MITM) using ARP spoofing and enabling packet forwarding, the tool intercepts DNS responses and modifies them in real-time. For example, it can redirect requests to www.bing.com to a custom web server hosted locally, such as an Apache2 server which is hosted at your linux machine. This demonstrates how DNS spoofing can be used to deceive users by directing them to unauthorized or malicious websites
