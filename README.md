#  System Design for ML

##  Day 01: Client-Server Architecture & Proxies

### 1. The Core: Request & Response Model
*Client-Server Architecture is the fundamental building block of the web.It is a distributed framework that divides tasks between service providers (**Servers**) and service requesters (**Clients**)

* **The Client:** A front-end application (web browser or mobile app) that initiates a request for data or an action.
* **The Server:** A powerful machine running 24/7, waiting to process requests, perform **CRUD** operations, and return a response.



---

### 2. Identity on the Web: IP & DNS
Computers identify each other using **IP Addresses**, which act like digital phone numbers. 
Since humans prefer names over numbers, we use **DNS**.

* **IP Address:** A unique identifier for every machine on the internet.
* **DNS (Domain Name System):** A distributed database that maps human-friendly domain names to numerical IP addresses.
* **Workflow:** When you type a URL, the browser first asks the DNS for the IP; once retrieved, it establishes a direct connection to the actual server.



---

### 3. Intermediaries: Proxy vs. Reverse Proxy
Proxies act as middlemen to handle **Security, Privacy, and Speed**.

#### **A. Forward Proxy (Protects the Client)**
* Represents the client and sits between a private network and the internet.
* **Anonymity:** The server only sees the proxy's IP, hiding the client's identity.
* **Caching:** Stores frequently accessed web pages to reduce **latency** (response time).



#### **B. Reverse Proxy (Protects the Server)**
* Represents the server and sits in front of backend servers to manage incoming traffic.
* **Security:** Hides the actual server IP from hackers to prevent **DDoS attacks**.
* **Load Balancing:** Distributes incoming requests across multiple servers (A, B, C) so no single machine is overloaded.
* **SSL Termination:** Handles encryption/decryption tasks so backend servers can focus on processing data.



---

### 4. Key Technical Terms
* **Latency:** The total time taken for a request to travel from the client to the server and back again.
* **TTL (Time to Live):** A timer set on cached data; once it expires, the data is deleted to ensure information does not become "stale".
* **VPN vs Proxy:** A VPN encrypts all internet traffic for higher security, while a proxy only forwards specific requests without necessarily encrypting them.

---


* **If the Model is Slow:** I check **Latency** to see if the delay is in the network (DNS/Proxy) or the **model inference** itself.We could add a forward proxy with caching for frequent inputs.
* **If Server Crashes during Peak Time:** We need a **Reverse Proxy** to act as a **Load Balancer** to distribute traffic so no single server is overloaded.
* **Protecting Model Infrastructure:** By using a **Reverse Proxy**, the client only interacts with the Proxy IP, keeping our internal backend hidden and secure.
