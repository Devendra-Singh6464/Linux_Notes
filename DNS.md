DNS, or **Domain Name System**, is like the phone-book of the internet. It translates human-friendly domain names (like `www.google.com`) into computer-friendly IP addresses (like `172.217.10.46`) so that your browser can load the correct website.

#### How It Works
1. **You Type a Domain Name**:  
    Let’s say you type `www.example.com` into your browser.
    
2. **Your Computer Asks the DNS Resolver**:  
    Your computer doesn’t know the IP address for `www.example.com`, so it asks a DNS resolver (usually provided by your Internet Service Provider or a public service like Google DNS).
    
3. **The Resolver Checks Its Cache**:  
    The resolver first checks if it already knows the IP address for `www.example.com`. If it does (from a previous request), it gives the answer immediately.
    
4. **If Not, the Resolver Asks the Root Servers**:  
    If the resolver doesn’t know, it asks the **root DNS servers**. These servers don’t know the exact IP address, but they can point to the **Top-Level Domain (TLD)** servers (like `.com`, `.org`, etc.).
    
5. **The Resolver Asks the TLD Servers**:  
    The resolver then asks the `.com` TLD server, which directs it to the **authoritative name servers** for `example.com`.
    
6. **The Authoritative Name Server Provides the IP**:  
    The authoritative name server for `example.com` finally provides the IP address for `www.example.com`.
    
7. **The Resolver Returns the IP to Your Computer**:  
    The resolver sends the IP address back to your computer, which then uses it to connect to `www.example.com`.
    
8. **Your Browser Loads the Website**:  
    Your browser uses the IP address to fetch the website and display it to you.
    

---

### Example in Steps:

1. You type `www.example.com` in your browser.
    
2. Your computer asks the DNS resolver: "What’s the IP for `www.example.com`?"
    
3. The resolver checks its cache. If it doesn’t know, it asks the root servers.
    
4. The root servers say: "Ask the `.com` TLD servers."
    
5. The `.com` TLD servers say: "Ask the authoritative name server for `example.com`."
    
6. The authoritative name server says: "The IP for `www.example.com` is `93.184.216.34`."
    
7. The resolver tells your computer: "The IP is `93.184.216.34`."
    
8. Your browser connects to `93.184.216.34` and loads the website.
    

---

### Why DNS is Important:

- **Human-Friendly**: You don’t need to remember numbers like `93.184.216.34`; you just type `www.example.com`.
    
- **Efficient**: DNS caches results, so repeated requests are faster.
    
- **Scalable**: It’s a distributed system, meaning no single server has to handle all requests.
    

In short, DNS is what makes the internet easy to use by turning names into numbers! 🌐

## **DNS Lookup**

**Types of DNS Lookup**:

- **Forward DNS Lookup**: Domain name → IP address.
    
- **Reverse DNS Lookup**: IP address → Domain name.

### 1. **Forward DNS Lookup**:

- You type a domain name (e.g., `www.google.com`) into your browser.
    
- Your computer performs a **Forward DNS Lookup** to find the IP address associated with that domain.
    
- Once the IP address is found, your browser uses it to connect to the website.

#### Example:

- You type `www.example.com` in your browser.
    
- A Forward DNS Lookup happens, and the DNS system returns the IP address `93.184.216.34`.
    
- Your browser connects to `93.184.216.34` and loads the website.

### 2. **Reverse DNS Lookup**:

This is the opposite of Forward DNS Lookup. It converts an **IP address** (like `93.184.216.34`) back into a **domain name** (like `www.example.com`). It’s like looking up a person’s name using their phone number.

#### How It Works:

- You have an IP address (e.g., `93.184.216.34`) and want to know which domain name it belongs to.
    
- A **Reverse DNS Lookup** is performed to find the domain name associated with that IP address.
    

#### Example:

- You have the IP address `93.184.216.34`.
    
- A Reverse DNS Lookup happens, and the DNS system returns the domain name `www.example.com`.

### **Fully Qualified Domain Name**

![[Pasted image 20250206114824.png]]

![[Pasted image 20250206115153.png]]

### DNS Record?

A DNS (Domain Name System) record is like an instruction manual for your domain name. It tells the internet how to handle requests for your domain, such as where to send emails or how to find your website.

Think of it as a set of directions that help people (and computers) find the right place when they type in your domain name.

### Common Types of DNS Records:

1. **A Record**: Points your domain to an IP address (where your website is hosted).
    
    - Example: `www.example.com` → `192.168.1.1`
        
2. **CNAME Record**: Acts like a nickname for your domain, pointing it to another domain name.
    
    - Example: `shop.example.com` → `www.example.com`
        
3. **MX Record**: Directs emails to the right mail server.
    
    - Example: Emails sent to `@example.com` → `mail.example.com`
        
4. **TXT Record**: Used for verification or security purposes (like proving you own the domain).
    
    - Example: Adding a Google verification code to prove ownership.
        
5. **NS Record**: Specifies which nameservers are responsible for your domain.
    
    - Example: `example.com` → `ns1.yourhostingprovider.com`

- Types of DNS Records
DNS records store information about a domain. The most common ones are:

|**Record Type**|**Purpose**|**Example**|
|---|---|---|
|**A Record**|Maps a domain to an IPv4 address|`example.com → 192.168.1.1`|
|**AAAA Record**|Maps a domain to an IPv6 address|`example.com → 2606:2800:220:1:248:1893:25c8:1946`|
|**CNAME Record**|Alias for another domain|`www.example.com → example.com`|
|**MX Record**|Mail server for a domain|`mail.example.com`|
|**TXT Record**|Stores text data (e.g., SPF, DKIM, security)|`v=spf1 include:_spf.google.com ~all`|
|**NS Record**|Specifies name servers for a domain|`ns1.example.com, ns2.example.com`|
|**PTR Record**|Reverse DNS (IP → Domain)|`192.168.1.1 → example.com`|

### DNS Records Work

Imagine your domain name is **[www.example.com](http://www.example.com/)**, and you want people to:

7. Visit your website.
    
8. Send emails to you.
    
9. Access your online store.
    

Here’s how DNS records help:

10. **A Record**: Tells the internet where your website is hosted.
    
    - `www.example.com` → `192.168.1.1` (your web server’s IP address).
        
11. **MX Record**: Tells email servers where to deliver emails.
    
    - Emails sent to `@example.com` → `mail.example.com`.
        
12. **CNAME Record**: Redirects your online store to your main website.
    
    - `shop.example.com` → `www.example.com`.
13.  **TXT Record**: Proves you own the domain for services like Google Workspace.
    
    - Adds a verification code like `google-site-verification=abc123`.

### Nameservers

Nameservers are like the **internet’s phonebook**. They help connect your domain name (e.g., `www.example.com`) to the actual server where your website is hosted. Without nameservers, no one would know where to find your website!

### How Nameservers Work:

14. **You buy a domain name**: Let’s say you buy `www.example.com`.
    
15. **You set up hosting**: Your website’s files are stored on a server (e.g., at a hosting company like Bluehost or AWS).
    
16. **You point your domain to nameservers**: You tell your domain to use the nameservers provided by your hosting company.
    

When someone types `www.example.com` in their browser:

17. The browser asks the nameserver, _“Where is `www.example.com`?”_
    
18. The nameserver replies, _“It’s at this IP address (e.g., `192.168.1.1`).”_
    
19.  The browser then connects to that IP address and loads your website.

### Real-Life Example:

Let’s say you buy a domain (`www.mycoffeeshop.com`) and host your website with a company like Bluehost. Bluehost gives you their nameservers:

- `ns1.bluehost.com`
    
- `ns2.bluehost.com`
    

You update your domain settings to use these nameservers. Now:

- When someone types `www.mycoffeeshop.com`, the nameservers tell the browser where to find your website (e.g., at IP address `192.168.1.1`).

*NOTE: In short, nameservers are the bridge between your domain name and your website’s server. They make sure visitors can find your website easily! *

### **1. DNS Load Balancing**

- **What it is**: DNS Load Balancing distributes incoming traffic across multiple servers to prevent any single server from being overwhelmed. It improves performance and ensures efficient use of resources.
    
- **How it works**: When a user tries to access a website, the DNS server returns multiple IP addresses (for different servers) in a rotating order. The user’s device connects to one of these IP addresses.
    

#### **Example**:

- A website (`example.com`) has three servers with IPs:
    
    - Server 1: `192.168.1.1`
        
    - Server 2: `192.168.1.2`
        
    - Server 3: `192.168.1.3`
        
- When users visit `example.com`, the DNS server rotates the order of IPs:
    
    - User 1 gets `192.168.1.1`
        
    - User 2 gets `192.168.1.2`
        
    - User 3 gets `192.168.1.3`
        
    - User 4 gets `192.168.1.1` again (and so on).
        
- This ensures traffic is evenly distributed across all servers.
    

---

### **2. DNS Failover**

- **What it is**: DNS Failover ensures that if one server goes down, users are automatically redirected to a working server. It improves reliability and prevents downtime.
    
- **How it works**: The DNS server monitors the health of servers. If a server fails, it stops directing traffic to that server and sends users to a backup server instead.
    

#### **Example**:

- A website (`example.com`) has two servers:
    
    - Primary Server: `192.168.1.1`
        
    - Backup Server: `192.168.1.2`
        
- Normally, users are directed to the primary server (`192.168.1.1`).
    
- If the primary server goes down, the DNS server detects the failure and starts directing users to the backup server (`192.168.1.2`).
    
- Users don’t experience downtime because they’re automatically redirected to the working server.
    

---

### **How DNS Load Balancing and Failover Work Together**

- **Load Balancing**: Distributes traffic evenly across multiple servers.
    
- **Failover**: Ensures traffic is redirected to working servers if one fails.
    

#### **Combined Example**:

- A website (`example.com`) has three servers:
    
    - Server 1: `192.168.1.1`
        
    - Server 2: `192.168.1.2`
        
    - Server 3: `192.168.1.3`
        
- **Load Balancing**: Traffic is distributed across all three servers.
    
- **Failover**: If Server 1 goes down, the DNS server stops directing traffic to it and distributes traffic only between Server 2 and Server 3.

 # What is a Proxy

A **proxy** is like a **middleman** or a **gatekeeper** between you and the internet. When you use a proxy, your internet requests (like visiting a website) go through the proxy server first, and then the proxy server forwards your request to the website. The website sees the proxy server's information instead of yours.


### **Real-Life Example**

Imagine you want to send a letter to a friend, but you don’t want them to know it’s from you. So, you give the letter to someone else (the proxy) to deliver it for you. Your friend only sees the person who delivered the letter, not you.


### **How Does a Proxy Work?**

1. **You**: You want to visit a website (e.g., `example.com`).
    
2. **Proxy Server**: Instead of connecting directly to the website, you connect to the proxy server.
    
3. **Proxy Requests**: The proxy server sends the request to the website on your behalf.
    
4. **Website Response**: The website sends the response back to the proxy server.
    
5. **Proxy Delivers**: The proxy server sends the response back to you.


### **Why Use a Proxy?**

1. **Hide Your Identity**:
    
    - The website sees the proxy server's IP address, not yours. This helps protect your privacy.
        
2. **Access Blocked Content**:
    
    - If a website is blocked in your country, you can use a proxy server in another country to access it.
        
3. **Improve Speed**:
    
    - Some proxies cache (save) website data, so if someone else has already visited the site, it loads faster for you.
        
4. **Security**:
    
    - Proxies can filter out malicious content or block harmful websites.

### **Types of Proxies**

1. **Forward Proxy**:
    
    - Used by clients (like you) to access the internet.
        
    - Example: A company might use a forward proxy to control employee internet access.
        
2. **Reverse Proxy**:
    
    - Used by websites to handle incoming traffic.
        
    - Example: A website might use a reverse proxy to balance traffic or improve security.
        
3. **Transparent Proxy**:
    
    - Works without you knowing. Often used in schools or offices to filter content.
        
4. **Anonymous Proxy**:
    
    - Hides your IP address but tells the website that you’re using a proxy.
        
5. **High Anonymity Proxy**:
    
    - Completely hides your identity and doesn’t reveal that you’re using a proxy.
        


### Example of Proxy in Action
- You want to visit example.com.

* You connect to a proxy server (e.g., proxy.com).

* The proxy server visits example.com for you.

* example.com sees the proxy server’s IP address, not yours.

* The proxy server sends the website’s content back to you.


Reference link:
https://kripeshadwani.com/dns-records-explained/#3-what-is-a-hostname-