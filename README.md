# Web_App_SIEM_Tool
Design and implementation of a web app SIEM tool capable of detecting common web attacks like sql injection, cross site scripting, command injection using Elastic stack

# Lightweight Security Information and Event Management (SIEM) Tool
A Project for Web Application Security
This repository contains the documentation, configuration files, and key findings for a project focused on the design and implementation of a lightweight SIEM tool. The tool is designed to provide cost-effective, real-time security monitoring for web applications in environments with limited resources, such as those found in Small to Medium-sized Enterprises (SMEs).

The project leverages the Elastic Stack (Filebeat, Elasticsearch, and Kibana) to collect, analyze, and visualise security events, enabling the detection of common web attacks with high accuracy and minimal system overhead.

🚀 Project Motivation
Traditional enterprise-grade SIEM solutions are often prohibitively expensive, complex, and resource-intensive, placing them out of reach for many organisations. This project addresses this gap by demonstrating that a robust and effective SIEM can be built using powerful, open-source components of the Elastic Stack, providing a viable and affordable alternative.

✨ Key Features
Real-time Log Collection: Utilises Filebeat to efficiently ship web server logs from the host to the central SIEM.

Threat Detection: Detects common web attacks including:

SQL Injection (SQLi)

Cross-Site Scripting (XSS)

Directory Traversal

Brute-force attacks

Automated Alerting: Configured alerts in Kibana to notify a Security Analyst via email or other channels when a threat is detected.

Intuitive Dashboards: Provides visual dashboards in Kibana for an at-a-glance view of security events, attack trends, and log activity.

Lightweight Architecture: Designed to operate with a low resource footprint, making it suitable for deployment on a single, moderately provisioned host.

🏛️ System Architecture
The project's architecture is built around three core components of the Elastic Stack:

Filebeat: Installed on the web server host (e.g., a Windows 11 machine), it acts as a lightweight log shipper. It monitors log files in real-time and forwards the data directly to Elasticsearch.

Elasticsearch: The central data store and analytical engine. It ingests, indexes, and stores the log data. Ingest Pipelines are used for basic parsing and enrichment before the data is indexed.

Kibana: The visualisation layer. It provides dashboards for monitoring, a management console for creating detection rules, and an alerting engine to send notifications.

⚙️ Prerequisites
To replicate this project, you will need to set up a virtual or physical machine with the following software installed:

Operating System: Windows 11 (or a similar Linux distribution)

Docker: For running the Damn Vulnerable Web Application (DVWA)

Elasticsearch: Version 8.9.2

Kibana: Version 8.9.2

Filebeat: Version 8.9.2

🏁 Installation and Setup

1. Setup the Elastic Stack
Follow the official documentation to install Elasticsearch, Kibana, and Filebeat on your host machine. Ensure all services are running and that Kibana is connected to Elasticsearch.

2. Configure Filebeat
Edit the filebeat.yml configuration file provided in this repository.

Update the paths to point to your web application's log files.

Update the output.elasticsearch section with your Elasticsearch host and credentials.

Start the Filebeat service to begin shipping logs.

3. Configure Kibana
Import the Kibana dashboards and detection rules provided in this repository's configuration files.

Ensure the alerting system is configured with your desired notification methods (e.g., email or a webhook for Slack).

4. Simulate Attacks (Testing)
Start the DVWA container using Docker.

Access the DVWA through your web browser and perform various attacks such as SQL Injection and XSS.

Observe the logs being ingested into Elasticsearch and watch for alerts to be triggered in Kibana.

📈 Project Results Summary
The SIEM tool was rigorously tested against a series of simulated attacks. The key performance metrics achieved are:

High Accuracy: The detection rules demonstrated high precision and recall, with F1-Scores above 0.93 for all tested attack types (SQLi, XSS, Directory Traversal, Brute-force).

Low Resource Utilisation: The system proved to be genuinely lightweight, with Filebeat consuming minimal resources and Elasticsearch operating efficiently on a single-node setup.

Low Alert Latency: Alerts were consistently delivered within an average of 18 seconds from the moment the malicious event was logged, enabling near real-time response.

👨‍💻 Future Work
This project serves as a robust foundation. Potential future enhancements could include:

Expanded Detection: Incorporating machine learning-based detection for anomaly and behavioural analysis to catch unknown threats.

SOAR Integration: Implementing automated response capabilities (e.g., IP blocking) to move beyond detection and into active defence.

Multi-Source Log Integration: Adding support for other log types beyond web server logs (e.g., firewall logs, system logs).

📄 License
This project is licensed under the MIT License.

🙏 Acknowledgements
The developers and community of the Elastic Stack (Elasticsearch, Kibana, Filebeat).

The developers of Damn Vulnerable Web Application (DVWA) for providing a safe environment for penetration testing.