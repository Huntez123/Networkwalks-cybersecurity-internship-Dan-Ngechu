Week 01 — Cybersecurity Lab Setup

Project Overview

This project involved setting up a practical cybersecurity testing laboratory using Oracle VirtualBox and Kali Linux.

The lab provides an isolated environment for practicing networking, cybersecurity, ethical hacking, and future security testing activities.

Objectives

The objectives of this lab were to:

- Set up Oracle VirtualBox as the virtualization platform.
- Configure Kali Linux as the attacking/hacker machine.
- Create a custom NAT Network using the `10.0.0.0/24` subnet.
- Configure Kali Linux with the IP address `10.0.0.2/24`.
- Provide Internet connectivity to the Kali Linux virtual machine.
- Enable clipboard sharing and file drag-and-drop.
- Configure a shared folder between the host machine and Kali Linux.
- Create a clean snapshot of the configured Kali Linux virtual machine.

Lab Environment

| Component | Configuration |
|---|---|
| Host Operating System | Windows |
| Virtualization Platform | Oracle VirtualBox |
| Attacking Machine | Kali Linux |
| Network Type | NAT Network |
| Network | `10.0.0.0/24` |
| Kali Linux IP | `10.0.0.2/24` |
| Default Gateway | `10.0.0.1` |
| DNS | `8.8.8.8`, `1.1.1.1` |
| Shared Folder | `/downloads` |

Network Configuration

A custom VirtualBox NAT Network named `NatNetwork` was configured using the following network:

- Network: `10.0.0.0/24`
- Gateway: `10.0.0.1`
- DHCP: Disabled

DHCP was disabled so that Kali Linux could use the required static address:

`10.0.0.2/24`

Kali Linux Configuration

The Kali Linux network connection was configured using NetworkManager.

The following configuration was applied:

- IP Address: `10.0.0.2/24`
- Gateway: `10.0.0.1`
- DNS: `8.8.8.8`, `1.1.1.1`
- Connection: `Wired connection 1`
- Interface: `eth0`

The configuration was verified successfully before activating the network connection.

Network Verification

The configured network was tested from Kali Linux.

Gateway Test

```bash
ping -c 3 10.0.0.1
```

The gateway responded successfully.

Internet Connectivity Test

```bash
ping -c 3 8.8.8.8
```

Internet connectivity was successfully verified.

DNS Resolution Test

```bash
ping -c 4 google.com
```

DNS resolution was confirmed and Internet connectivity was available.

Clipboard and Drag-and-Drop

VirtualBox integration features were enabled for the Kali Linux virtual machine.

The following features were configured:

- Shared Clipboard: Bidirectional
- Drag and Drop: Bidirectional

Both features were tested and confirmed to be working.

Shared Folder Configuration

A shared folder was configured between the Windows host and Kali Linux.

Windows Host

`C:\downloads`

Kali Linux

`/media/sf_downloads`

A `/downloads` path was also created in Kali Linux as a convenient link to the VirtualBox shared folder.

The shared folder was tested by creating a text file on the Windows host and reading it successfully from Kali Linux.

VM Snapshot

After completing the lab configuration, a clean snapshot of the Kali Linux virtual machine was created.

Snapshot Name

`Week1 - Clean Lab Setup`

The snapshot preserves the configured state of the laboratory for future cybersecurity exercises.

Troubleshooting

During the static IP configuration, Kali Linux initially failed to activate the required `10.0.0.2/24` configuration.

The Networkwalks troubleshooting guidance for the Kali Linux and VirtualBox environment was followed.

The following NetworkManager setting was applied:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

The network connection was then restarted:

```bash
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

After applying the configuration, the connection activated successfully and Kali Linux operated with the required `10.0.0.2/24` address.

Challenges Encountered

The main challenge during the lab setup was activating the required static IP address on the Kali Linux virtual machine.

The issue was resolved by applying the NetworkManager Duplicate Address Detection (DAD) workaround recommended in the Networkwalks lab documentation.

This provided practical experience in troubleshooting Linux network configuration and VirtualBox NAT Network connectivity.

Evidence

Screenshots documenting the lab setup are maintained in the `screenshots/` directory.

The evidence includes:

1. Kali Linux network configuration
2. VirtualBox NAT Network configuration
3. Shared folder configuration
4. Shared folder functionality test
5. Kali Linux VM snapshot

Learning Outcomes

By completing this lab, I gained practical experience in:

- Virtual machine deployment and configuration
- VirtualBox NAT Network configuration
- Linux network configuration
- Static IP addressing
- Gateway and Internet connectivity testing
- DNS resolution testing
- VirtualBox integration features
- Host-to-VM shared folders
- Linux network troubleshooting
- Virtual machine snapshots
- Technical documentation

Lab Status

**Status: Completed**

The required Phase 1 cybersecurity laboratory environment has been successfully configured.

Future Work

The Networkwalks lab documentation identifies additional virtual machines and inter-machine ping testing as Phase 2, which is optional/future work.

Future exercises may expand the laboratory with additional virtual machines for cybersecurity and ethical hacking practice.

Conclusion

The Week 01 cybersecurity laboratory was successfully established using Oracle VirtualBox and Kali Linux.

The final environment provides a practical foundation for future cybersecurity labs, networking exercises, ethical hacking activities, and Capture The Flag (CTF) challenges.

---

**Networkwalks Academy — Cybersecurity Internship**  
**Week 01 Practical Lab**
