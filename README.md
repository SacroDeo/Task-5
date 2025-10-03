
# PCAP Detailed Analyzer

This project provides a Python script to analyze `.pcap` or `.pcapng` files and automatically generate a **detailed PDF report** explaining the contents of the capture file. The report includes protocol statistics, communication patterns, port usage, and potential security insights.

---

## Features

* ✅ Parses `.pcap` / `.pcapng` files using **Scapy**
* ✅ Generates a structured **PDF report** with:

  * Total packet count
  * Protocol distribution (IP, TCP, UDP, ICMP, ARP, etc.)
  * Top source and destination IPs
  * Top used ports (services)
  * Suspicious activity detection (ICMP floods, port scans, sensitive port usage, etc.)
  * Human-readable explanations for each section
* ✅ Lightweight and easy to use (single script, no external tools like Wireshark required)

---

## Requirements

Install the dependencies before running:

```bash
pip install scapy reportlab
```

---

## Usage

1. Place your `.pcap` or `.pcapng` file in the same folder as the script.
2. Run the script:

   ```bash
   python pcap_detailed_report.py
   ```
3. The script will automatically:

   * Find the first `.pcap`/`.pcapng` file in the folder
   * Analyze the capture
   * Generate a PDF report named **`pcap_detailed_report.pdf`**

---

## Example Output

The generated PDF contains:

### 📊 Protocol Analysis

Shows how many packets belong to TCP, UDP, ICMP, ARP, etc.
*High ICMP traffic might suggest scanning; ARP anomalies could mean spoofing.*

### 🌐 Top Source & Destination IPs

Lists the most active IPs (e.g., servers, clients, or suspicious hosts).
*Heavy talkers may represent servers, scanners, or malicious hosts depending on context.*

### 🔌 Port Distribution

Displays the most frequently used ports.
*Ports 80/443 → Web traffic; unusual or high ports may indicate scans or custom apps.*

### 🔒 Security Insights

Highlights suspicious behavior such as:

* Excessive ICMP traffic → possible ping sweep/DoS
* Many ports contacted → possible port scan
* Sensitive ports (22, 23, 445) → possible unauthorized access attempts

### ✅ Conclusion

Summarizes findings and recommends deeper review with Wireshark or IDS if needed.

---

## Sample Report

An example generated report is included: **`pcap_detailed_report.pdf`**

---

## Next Steps

Future improvements can include:

* Reverse DNS lookups (mapping IPs to websites/services)
* Extracting HTTP Host headers & TLS SNI for exact domain names
* Adding charts (pie charts for protocols, bar charts for top IPs/ports)

