# IoT security

## IoT threats

- **Lack of security**
  - Speed at which IoT is advancing makes it harder to keep up with evolving security requirements.
  - Being short on processing power and memory leads to lack of security solutions and encryption protocols.
- **Vulnerable interfaces**
  - For both device interfaces and other interfaces (e.g. cloud) it interacts with
  - E.g. lack of authentication/authorization, lacking or weak encryption, and a lack of input and output filtering.
- **Physical security risk**
  - Cannot secure them as traditional devices by e.g. the storage of routers in secure cabinets
- **Lack of vendor support**
  - The support of a certain device may get discontinued
- **Difficult to update firmware and OS**
  - Some require manual intervention to be upgraded, some cannot be upgraded at all
  - Being compliant makes harder to do changes to e.g. medical devices.
- **Interoperability issues**
  - Interoperability: "the ability to make systems and organizations work together" | [Wikipedia](https://en.wikipedia.org/wiki/Interoperability)
  - Each solution provides its own IoT infrastructure, devices, APIs, and data formats
  - Caused by competitive nature of IoT e.g. vendor lock-in

## OWASP Top 10 IoT (2018)

- OWASP Internet of Things Top Ten was introduced in 2004 and updated in [2018](https://owasp.org/www-pdf-archive/OWASP-IoT-Top-10-2018-final.pdf)

1. **Weak, guessable, or hardcoded passwords**
   - Use of easily bruteforced, publicly available, or unchangeable credentials
   - Including [backdoor](./../07-malware/malware-overview.md#backdoor)s in firmware or client software that grants unauthorized access to deployed systems
2. **Insecure network services**
   - Unneeded or insecure network services running on the device itself
   - Bigger threat for those that are expose to the internet
   - Allows compromise confidentiality, integrity/authenticity, or availability of information or allow unauthorized remote control...
3. **Insecure ecosystem interfaces**
   - Includes web, backend API, cloud, or mobile interfaces outside of the device
   - Allows compromise of the device or its related components.
   - E.g. lack of authentication/authorization, lacking or weak encryption, a lack of input and output filtering.
4. **Lack of secure update mechanism**
   - Lack of firmware validation on device
   - Lack of secure delivery (un-encrypted in transit)
   - Lack of anti-rollback mechanisms
   - Lack of notifications of security changes due to updates.
5. **Use of insecure or outdated components**
   - Use of deprecated or insecure software components/libraries
   - Insecure customization of operating system platforms
   - Use of third-party software or hardware components from a compromised supply chain
6. **Insufficient privacy protection**
   - Use of users personal information insecurely, improperly, or without permission.
7. **Insecure data transfer and storage**
   - Lack of encryption or access control of sensitive data
   - Can be anywhere within the ecosystem e.g. at rest, in transit, or during processing.
8. **Lack of device management**
   - Lack of security support on devices deployed in production
   - Capabilities include e.g. asset management, update management, secure decommissioning, systems monitoring, and response.
9. **Insecure default settings**
   - Can be shipped with insecure settings or without ability to make restrictions.
10. **Lack of physical hardening**
    - Easily accessible physically

## IoT attacks

- **Access control**
  - E.g. remote access control or gaining access to administration panels
- **BlueBorn Attack**
  - Amalgamation of techniques and attacks against known, already existing [Bluetooth vulnerabilities](./../09-wireless-networks/bluetooth.md#bluetooth-attacks)
- **Jamming Attack**
  - Also known as **signal jamming attack**
  - Jamming the signal to prevent the communication of devices
- **Man-in-the-middle attack**
  - E.g. by sniffing through [Foren6](https://github.com/cetic/foren6)
    - Passive sniffer
    - Reconstruct a visual and textual representation of network information to support real-world Internet of Thingl
- **HVAC attack**
  - Takes place when one hacks IoT devices in order to shut down air conditioning services.  
- [Backdoor](./../07-malware/malware-overview.md#backdoor) (not just IoT related)
- [Exploit kits](../07-malware/malware-overview.md#exploit-kit)
- [Replay attack](./../06-system-hacking/cracking-passwords-overview.md#replay-attack)
- [Ransomware](./../07-malware/malware-overview.md#ransomware) attack
- [Privilege escalation](./../06-system-hacking/escalating-privileges.md)
- [Side channel attack](./../16-cloud-computing/cloud-security.md#side-channel-attacks)
- [Web application attacks](./../13-web-applications/hacking-web-applications.md), [web server attacks](./../12-web-servers/web-server-threats-and-attacks.md)
- [Cloud computing attacks](./../16-cloud-computing/cloud-security.md#cloud-computing-attacks)
- [Mobile application threats](./../17-mobile-platforms/mobile-attacks.md)
- [DoS / DDoS](./../13-web-applications/denial-of-service.md)
- Forged malicious devices
- Resetting to an insecure state
- Removal of storage media
- Firmware attack
- Network service attacks
- Unencrypted local data storage
- Confidentiality and integrity issues
- Malicious updates
- Insecure APIs
- Eavesdropping
- Sybil attack

### Rolling code attack

- Also known as **hopping code** attack.
- Used in keyless entry systems such as garage door openers and keyless car entry systems.
- Attacker capture signal from transmitter device, simultaneously blocking the receiver to receive the signal
- Attacker uses the signal to gain unauthorized access
- E.g. stealing car with captured signal
- Tools include [HackRF One](https://greatscottgadgets.com/hackrf/one/) hardware tool.

### Firmware extraction

- Allows looking for data in filesystem or reverse engineering it for vulnerabilities.
- Flow example:
  1. [`binwalk`](https://github.com/ReFirmLabs/binwalk) is a common tool for it found on Kali Linux.
  2. [`firmwalker`](https://github.com/craigz28/firmwalker) to list vulnerabilities by scanning all files.

### Device memory containing credentials

- Can be used for reading/manipulating data
- Allows pushing firmware updates
- Enables usage of devices to other devices in the network

## Hacking Methodology

### Information gathering

- IP address
- Running protocols
- Open ports
- Type of device
- Vendor
- [Shodan](https://www.shodan.io/) is a helpful search engine for IoT

### Vulnerability scanning

- Scanning the network and devices to find vulnerabilities
- Search for weak password
- Software and firmware vulnerabilities
- Tools
  - [`nmap`](../03-scanning-networks/scanning-tools.md#nmap)
  - [`hping`](./../03-scanning-networks/scanning-tools.md#hping)
  - [Firmalyzer](https://www.firmalyzer.com/)
    - Security assessments with risk analysis in IoT networks
    - Proprietary platform

### Attack

- Exploiting vulnerabilities
- E.g. running [rolling code attack](#rolling-code-attack)

### Gain access

- Gain unauthorized access
- Privilege escalation
- Install backdoor

### Maintain attack

- Logging out
- Clearing logs
- Covering tracks

## Countermeasures

- Firmware update
- Block unnecessary ports
- Disable telnet as it's insecure protocol
- Use encrypted communication (SSL/TLS)
- Use strong password
- Encrypt drives
- Periodic assessment of devices
- Secure password recovery
- Two-Factor Authentication
- Disable UPnP
