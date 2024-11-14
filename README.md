# Analyzing-A-Network-Attack
<h2>Analyzing network attacks activity</h2>
Review the following scenario. Then complete the step-by-step instructions.

You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.
<h2>Step 1: Accessing the template </h2>

[Cybersecurity incident report.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285915/Cybersecurity.incident.report.pdf)

## Incident Analysis and Explanation   <a name="Incident-Analysis-and-Explanation">
Type of Attack: The attack in question is likely a SYN Flood Attack, which is a type of Denial-of-Service (DoS) attack.

Potential Explanation for Connection Timeout Error Message: One potential explanation for the website's connection timeout error message is that the web server was overwhelmed by a large number of incoming TCP SYN requests, preventing it from responding to legitimate requests.

Logs Indicate: The logs show a large number of TCP SYN requests originating from an unfamiliar IP address. These requests are likely attempts to open many half-open connections, thereby consuming server resources and causing legitimate connection attempts to timeout.

Event Classification: This event could be a Denial-of-Service (DoS) attack aimed at disrupting the normal operation of the web server by exhausting its resources.

## Summary for Manager:   <a name="Summary-for-Manager:">
Scenario:

- Incident: Automated alert indicated a problem with the web server; connection timeout error when attempting to access the website.

- Cause: Large number of TCP SYN requests from an unfamiliar IP address, overwhelming the server.

Events and Symptoms Identified:

- Automated alert from monitoring system.

- Connection timeout error message when visiting the website.

- Packet sniffer revealed an abnormally high volume of TCP SYN requests from a single IP address.

Actions Taken:

1. Temporarily took the server offline to allow it to recover.

2. Configured the firewall to block the IP address sending the abnormal SYN requests.

Current Status: The server has been taken offline to recover, and a temporary firewall rule is in place to block the offending IP address.

Investigation Findings:

- The server was receiving a large number of TCP SYN requests, which it could not handle, leading to a connection timeout.

- The source of these SYN requests was an unfamiliar IP address, indicating a possible SYN flood attack.

Next Steps in Troubleshooting and Resolving the Issue:

1. Permanent Mitigation: Implement rate limiting or SYN cookies to protect against SYN flood attacks.

2. Network Monitoring: Continue monitoring for suspicious traffic patterns and adjust firewall rules as necessary.

3. Incident Response Plan: Develop or update the incident response plan to include specific steps for handling similar attacks in the future.

Suspected Root Cause: The suspected root cause is a SYN flood attack from a malicious actor attempting to disrupt service by overwhelming the web server with SYN requests.

-------------------

## Explanation and Analysis of the Attack   <a name="Explanation-and-Analysis-of-the-Attack">
Summary of How the Attack is Causing the Website to Malfunction: The attack, likely a SYN Flood Attack, is causing the website to malfunction by overwhelming the web server with an abnormally large number of TCP SYN requests. This flood of requests consumes the server's resources, preventing it from responding to legitimate connection attempts, which results in a connection timeout error for users trying to access the website.

### Three Steps of the TCP Handshake:

SYN (Synchronize): The client initiates a connection by sending a TCP SYN (synchronize) packet to the server, indicating a desire to establish a connection.

SYN-ACK (Synchronize-Acknowledge): The server responds to the client's SYN packet with a SYN-ACK (synchronize-acknowledge) packet, indicating that it received the SYN request and is ready to establish the connection.

ACK (Acknowledge): The client sends an ACK (acknowledge) packet back to the server, confirming that it received the server's SYN-ACK response. This completes the three-way handshake, and the connection is established.

What Happens When a Malicious Actor Sends a Large Number of SYN Packets All at Once: When a malicious actor sends a large number of SYN packets all at once, the server allocates resources for each incoming SYN request. However, because the attacker does not complete the three-way handshake, these half-open connections consume the server's resources, preventing it from handling legitimate traffic. This type of attack exhausts the server's ability to respond to legitimate SYN requests, leading to a denial of service.

Explanation of What the Logs Indicate and How That Affects the Server: The logs indicate a large number of incoming TCP SYN requests from an unfamiliar IP address. This abnormal traffic pattern suggests that the server is under a SYN flood attack. The server is overwhelmed by these requests, causing it to lose the ability to respond to legitimate traffic. As a result, users attempting to access the website experience connection timeouts because the server cannot complete the necessary TCP handshake to establish a connection.

### Summary for Manager:
1. Incident: Automated alert indicating a problem with the web server; connection timeout error when accessing the website.

2. Cause: Large number of TCP SYN requests from an unfamiliar IP address, overwhelming the server.

3. Effect on Server: The server is unable to handle legitimate connection requests due to resource exhaustion caused by the SYN flood attack.

4. Immediate Actions: Took the server offline to allow it to recover and blocked the offending IP address using the firewall.

5. Next Steps: Implement more robust defenses such as rate limiting, SYN cookies, and continuous monitoring to prevent future SYN flood attacks

<h2>Step 2: Accessing supporting documents </h2>

[Wireshark TCP_HTTP log - TCP log.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285917/Wireshark.TCP_HTTP.log.-.TCP.log.pdf)

[How to read the Wireshark TCP_HTTP log.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285918/How.to.read.the.Wireshark.TCP_HTTP.log.pdf)


<h2>Step 3: Identify the type of attack causing this network interruption </h2>

Reflect on the types of network intrusion attacks that you have learned about in this course so far. As a security analyst, identifying the type of network attack based on the incident is the first step to managing the attack and preventing similar attacks in the future. 

Here are some questions to consider when determining what type of attack occurred: 

●What do you currently understand about network attacks?

●Which type of attack would likely result in the symptoms described in the scenario? 

●What is the difference between a denial of service (DoS) and distributed denial of service (DDoS)? 

●Why is the website taking a long time to load and reporting a connection timeout error?

Review the linked Wireshark log file excerpt and try to identify patterns in the logged network traffic. Analyze the patterns to determine which type of network attack occurred. Write your analysis in section one of the Cybersecurity incident report template provided. Describe your analysis and include the type of attack and what information led you to your decision.

[Cybersecurity incident report Response.pdf](https://github.com/kalemriah/Analyzing-A-Network-Attack/files/12285921/Cybersecurity.incident.report.Response.pdf)

--------------------
### Cybersecurity Incident Report - Section One: Analysis and Explanation of the Attack

1. Type of Attack: The network interruption was caused by a SYN Flood Attack. This is evident from the Wireshark capture log, which shows repeated TCP SYN packets from a single source IP address (203.0.113.0) to the destination IP address (192.0.2.1) on port 443.

2. Understanding of Network Attacks from the Wireshark Reading: From the Wireshark reading, it is clear that a SYN flood attack is occurring. This type of attack involves sending a large number of TCP SYN packets to initiate connections but not completing the handshake. This floods the server with half-open connections, exhausting its resources.

3. Likely Type of Attack Resulting in the Symptoms: The symptoms described in the scenario, such as network interruption and connection timeout errors, are consistent with a SYN Flood Attack. This type of attack aims to overwhelm the server, preventing it from handling legitimate requests.

4. Difference Between DoS and DDoS:
- Denial of Service (DoS): A DoS attack originates from a single source and aims to make a service unavailable by overwhelming it with traffic. This can include methods like SYN flood, ping of death, or other types of flooding attacks.

- Distributed Denial of Service (DDoS): A DDoS attack involves multiple sources (often a botnet) attacking a single target simultaneously. This makes the attack harder to mitigate because the traffic comes from many different locations, increasing its scale and impact.

5. Reason for Slow Website Loading and Connection Timeout: The website is taking a long time to load and is reporting a connection timeout error because the server is overwhelmed by the SYN flood attack. The high volume of SYN requests exhausts the server’s resources, preventing it from responding to legitimate traffic and completing TCP handshakes. As a result, users experience significant delays and timeouts when trying to connect to the website.

<h2>Step 4: Explain how the attack is causing the website to malfunction </h2>

●Describe how the network attack is causing problems in the worksheet. Review the network activity log, reflect on your answer to the prompts in the first section of this activity, and write a report in the space provided in the template. 

●When writing your report, discuss the network devices and activities that are involved in the interruption. Include the following information in your explanation:

●Describe the attack. What are the main symptoms or characteristics of this specific type of attack? 

●Explain how it affected the organization’s network. How does this specific network attack affect the website and how it functions?

●Describe the potential consequences of this attack and how it negatively affects the organization. 

●Optional: Suggest potential ways to secure the network so this attack can be prevented in the future.

---------------------

### Cybersecurity Incident Report - Section Two: Attack Analysis and Network Impact

Description of the Attack: The network interruption was caused by a SYN Flood Attack. This type of attack involves sending a large number of TCP SYN packets to a target server, overwhelming it with connection requests. The main symptoms of this attack include:

- A large volume of SYN packets observed in network traffic logs.

- Incomplete three-way handshakes, resulting in many half-open connections.

- Server resources being consumed, leading to legitimate connection attempts timing out.

Impact on the Organization’s Network: The SYN flood attack significantly affected the organization’s network, particularly the web server hosting the company’s sales and promotions website. The specific impacts included:

- Resource Exhaustion: The server was unable to handle the large volume of incoming SYN requests, leading to resource exhaustion.

- Connection Timeouts: Legitimate users experienced connection timeouts and were unable to access the website, impacting both employees and customers.

- Service Disruption: The continuous flood of SYN packets disrupted normal operations, preventing employees from searching for vacation packages and customers from accessing promotional information.

Potential Consequences of the Attack: The consequences of the SYN flood attack include:

- Operational Disruption: Employees were unable to perform their tasks efficiently due to the unavailability of the web server.

- Customer Dissatisfaction: Customers were unable to access the website, leading to potential loss of sales and damage to the company’s reputation.

- Financial Loss: The downtime could result in lost sales opportunities and increased costs associated with mitigating the attack and restoring normal operations.

- Security Concerns: The attack highlighted potential vulnerabilities in the network’s security, raising concerns about the organization's ability to protect against future attacks.

Potential Ways to Secure the Network: To prevent similar attacks in the future, the following measures can be implemented:

- Rate Limiting: Implement rate limiting to restrict the number of SYN requests a single IP address can send in a given time period.

- SYN Cookies: Enable SYN cookies on the server to handle SYN flood attacks by ensuring the server can continue to respond to legitimate requests even under attack.

- IP Filtering: Use IP filtering to block suspicious IP addresses and traffic patterns.

- DDoS Mitigation Services: Consider using DDoS mitigation services that can detect and mitigate large-scale attacks.

- Network Monitoring: Continuously monitor network traffic for abnormal patterns and set up alerts to detect potential attacks early.

This comprehensive analysis outlines the nature of the attack, its impact on the organization, and potential measures to enhance network security and prevent future incidents.
