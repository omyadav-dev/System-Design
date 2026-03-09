#  System Design for ML Engineers

## 📅 Day 01: Client-Server Architecture & Proxies

### 1. The Core: Request & Response Model
[cite_start]Client-Server Architecture is the fundamental building block of the web[cite: 7]. [cite_start]It is a distributed framework that divides tasks between service providers (**Servers**) and service requesters (**Clients**)[cite: 7].

* [cite_start]**The Client:** A front-end application (web browser or mobile app) that initiates a request for data or an action[cite: 13, 14, 16, 17].
* [cite_start]**The Server:** A powerful machine running 24/7, waiting to process requests, perform **CRUD** operations, and return a response[cite: 18, 19, 20].



---

### 2. Identity on the Web: IP & DNS
[cite_start]Computers identify each other using **IP Addresses**, which act like digital phone numbers[cite: 27, 28, 29]. [cite_start]Since humans prefer names over numbers, we use **DNS**[cite: 34, 35, 36].

* [cite_start]**IP Address:** A unique identifier for every machine on the internet[cite: 37].
* [cite_start]**DNS (Domain Name System):** A distributed database that maps human-friendly domain names to numerical IP addresses[cite: 38, 39, 40].
* [cite_start]**Workflow:** When you type a URL, the browser first asks the DNS for the IP; once retrieved, it establishes a direct connection to the actual server[cite: 41, 42, 43].



---

### 3. Intermediaries: Proxy vs. Reverse Proxy
[cite_start]Proxies act as middlemen to handle **Security, Privacy, and Speed**[cite: 51, 52, 53, 54].

#### **A. Forward Proxy (Protects the Client)**
* [cite_start]Represents the client and sits between a private network and the internet[cite: 55, 57].
* [cite_start]**Anonymity:** The server only sees the proxy's IP, hiding the client's identity[cite: 58, 59].
* [cite_start]**Caching:** Stores frequently accessed web pages to reduce **latency** (response time)[cite: 62].



#### **B. Reverse Proxy (Protects the Server)**
* [cite_start]Represents the server and sits in front of backend servers to manage incoming traffic[cite: 71, 72].
* [cite_start]**Security:** Hides the actual server IP from hackers to prevent **DDoS attacks**[cite: 74].
* [cite_start]**Load Balancing:** Distributes incoming requests across multiple servers (A, B, C) so no single machine is overloaded[cite: 75, 76, 78].
* [cite_start]**SSL Termination:** Handles encryption/decryption tasks so backend servers can focus on processing data[cite: 79, 80].



---

### 4. Key Technical Terms
* [cite_start]**Latency:** The total time taken for a request to travel from the client to the server and back again[cite: 107].
* [cite_start]**TTL (Time to Live):** A timer set on cached data; once it expires, the data is deleted to ensure information does not become "stale"[cite: 105, 106].
* [cite_start]**VPN vs Proxy:** A VPN encrypts all internet traffic for higher security, while a proxy only forwards specific requests without necessarily encrypting them[cite: 87, 88].

---


* [cite_start]**If the Model is Slow:** I check **Latency** to see if the delay is in the network (DNS/Proxy) or the **model inference** itself[cite: 114, 116]. [cite_start]We could add a forward proxy with caching for frequent inputs[cite: 117, 118].
* [cite_start]**If Server Crashes during Peak Time:** We need a **Reverse Proxy** to act as a **Load Balancer** to distribute traffic so no single server is overloaded[cite: 119, 120].
* [cite_start]**Protecting Model Infrastructure:** By using a **Reverse Proxy**, the client only interacts with the Proxy IP, keeping our internal backend hidden and secure[cite: 121, 122].
