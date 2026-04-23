# Service Investigation and Interaction Lab

## Summary

This lab focused on investigating an unknown service running on port 5040 on a Windows virtual machine. The objective was to analyze the service behavior using multiple techniques and attempt to identify it through scanning and manual interaction.

---

## Target Information

* Target IP: 10.0.2.3
* Operating System: Microsoft Windows (based on scan results)

---

## Tools Used

* Nmap (network scanning and service detection)
* Netcat (manual interaction)

---

## Initial Discovery

A previous scan identified port 5040 as open, but the service was unknown.

---

## Deep Service Scan

A targeted scan was performed using:

```bash
nmap -sV -sC -p 5040 10.0.2.3
```

### Results

* Port 5040 is open
* Service remains unknown

### Analysis

Even after using version detection and default scripts, Nmap was unable to identify the service. This suggests the service could be using a custom or restricted protocol.

---

## Manual Interaction

A connection was established using Netcat:

```bash
nc 10.0.2.3 5040
```

### Interaction Attempt

* Sent input: `GET /`
* No response was received

### Analysis

The service did not respond to HTTP-style requests, indicating it is not a standard web service and may require a specific communication format.

---

## Banner Grabbing

A banner grabbing attempt was performed:

```bash
nmap -p 5040 --script=banner 10.0.2.3
```

### Results

* No banner information was returned

### Analysis

The service did not reveal any identifying information, suggesting it is configured to minimize exposure or does not provide banner data.

---

## Aggressive Scan

An aggressive scan was conducted:

```bash
nmap -p 5040 -A -Pn 10.0.2.3
```

### Results

* Port 5040 remains open and unknown
* OS detection suggests Microsoft Windows (approx. 92% confidence)

### Analysis

Even with advanced scanning techniques, the service could not be identified. This indicates it may be a custom, internal, or restricted service that does not respond to standard probing methods.

---

## Conclusion

The service running on port 5040 was successfully investigated using multiple techniques, including scanning, script analysis, and manual interaction. Despite these efforts, the service could not be identified.

This outcome demonstrates that not all services can be easily recognized and highlights the importance of investigation and accurate documentation in cybersecurity analysis.

---

## Screenshots

Relevant screenshots for each step of the investigation are included in the `/screenshots` folder.



