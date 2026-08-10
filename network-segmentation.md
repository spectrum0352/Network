# ISO 27001:2022 | ISO 27002:2022

## Control 8.22: Segregation of Networks

### Control Attributes

* **Control Type:** #Preventive
* **Information Security Properties:** #Confidentiality, #Integrity, #Availability
* **Cybersecurity Concepts:** #Protect
* **Operational Capabilities:** #System_and_network_security
* **Security Domains:** #Protection

---

### Control Statement

Groups of information services, users, and information systems should be segregated in the organization’s networks.

---

### Requirement

Networks are one of the most critical components in information systems, making it essential to ensure their confidentiality, integrity, and availability. Based on business requirements, the network should establish defined boundaries with controlled ingress and egress traffic, adhering to the principle of least privilege/access by allowing only necessary traffic.

---

### Implementation

#### 1. Risk and Segmentation Strategy

There is always a risk of unauthorized access attempts on networks, which could lead to a loss of confidentiality and integrity for the network or the systems connected to it.

A large network presents an increased risk of security breaches, especially for large organizations operating across multiple geographical locations. First, it is crucial to isolate the organizational network from public networks (i.e., the Internet). Security can be managed more effectively if the organizational network is divided into physical or logical domains; tight security can then be enforced by implementing firewalls between these domains.

The most common method is segmenting the network into Virtual Local Area Networks (VLANs) as logical domains. These VLANs can be classified based on departments (most common) or physical locations (e.g., floors in a building), which carry different levels of criticality and sensitivity. For example, systems in the Finance department have a higher level of criticality than those in the Customer Service department.

Creating VLANs simplifies network management. Security can be further enhanced by implementing internal segmentation firewalls in addition to perimeter firewalls, which are used to segregate the organizational network from the Internet.

#### 2. Firewall Management and Network Perimeter

Perimeter firewalls can be utilized to protect the organization’s networks against unapproved ingress traffic while simultaneously allowing only required egress traffic—such as public access to organizational services, staff internet browsing, and incoming/outgoing organizational email.

Critical network domains (e.g., Data Centers and Operational Technology [OT] networks) should be segregated from general user networks for additional security using a Core Firewall. Next-Generation Firewall (NGFW) features, such as Intrusion Prevention Systems (IPS), should be enabled on core firewalls to protect critical networks from user networks.

#### 3. Wireless, Guest, and Specialized Networks

Wired and wireless networks should also be segregated by assigning separate VLANs for Wi-Fi networks. Because Wi-Fi networks extend beyond physical boundaries, it is important to implement secure Wi-Fi access protocols (such as WPA2 and WPA3) with identity-based authentication rather than pre-shared keys (PSK).

Guest networks must be isolated from all other internal networks and restricted to minimal access (Internet access only). Guest users should not be able to access internal networks, and employees should be discouraged from using guest networks.

#### 4. Network Modeling and Risk Control

An organization should utilize network modeling to determine the specific network zones required for its operational environment. A comprehensive risk assessment will determine the exact level of security needed for each zone. Sufficient separation of networks should ultimately be achieved through the implementation of controlled network connections and routing controls.

---

*Source: [https://www.linkedin.com/in/dipendas1979/*](https://www.linkedin.com/in/dipendas1979/)