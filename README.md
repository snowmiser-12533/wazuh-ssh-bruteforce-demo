# Wazuh SSH Brute-Force Detection Lab

## Overview
This project demonstrates the effectiveness of Wazuh, an open-source security monitoring platform, in detecting and responding to a simulated SSH brute-force attack. The lab follows an incident response approach and highlights both detection capabilities and practical implementation challenges.

## Objectives
- Simulate an SSH brute-force attack using Hydra
- Monitor authentication logs on a Linux system
- Detect suspicious activity using Wazuh
- Evaluate automated response mechanisms
- Identify configuration limitations and required adjustments

## Lab Environment
- Kali Linux (Attacker)
- Ubuntu Server (Target with SSH enabled)
- Wazuh Manager (Detection and analysis)
- Wazuh Agent (Installed on monitored endpoint)
- VirtualBox Host-Only Network (isolated lab environment)

> Note: A three-machine setup was required. Wazuh Manager and Agent were deployed on separate systems due to installation and operational constraints.

## Attack Simulation
The attacker system (Kali Linux) used Hydra to perform a brute-force attack against the SSH service (port 22) on the Ubuntu target. Multiple login attempts were generated using a password wordlist.

## Detection and Monitoring
Wazuh is preconfigured with rules designed to detect suspicious authentication behavior, including repeated failed login attempts.

- The Ubuntu system logged SSH authentication attempts
- The Wazuh agent collected and forwarded logs to the manager
- The Wazuh manager analyzed the logs using built-in detection rules
- Alerts were successfully generated for brute-force activity

## Response and Configuration Challenge
Although Wazuh successfully detected the attack, the automated response (blocking the attacker IP) did not initially trigger.

### Issue Identified:
- Default configuration detected the threat but did not enforce a firewall block

### Resolution:
- A rule/configuration adjustment was required to enable active response
- After updating the configuration, Wazuh successfully blocked the attacking IP

This step highlights that detection alone is not sufficient—**proper configuration of response mechanisms is critical**.

## Key Takeaways
- Wazuh provides strong out-of-the-box detection capabilities
- Brute-force attacks produce clear and detectable log patterns
- Active response features require proper configuration to function
- Lab architecture (separating manager and agent) impacts effectiveness
- Open-source tools can be highly effective when properly tuned

## Screenshots
(Add:
- VirtualBox 3-VM setup
- Hydra attack in progress
- Wazuh alerts dashboard
- Evidence of blocked IP)

## Author
Cybersecurity Graduate Student  
Incident Response Lab Project
