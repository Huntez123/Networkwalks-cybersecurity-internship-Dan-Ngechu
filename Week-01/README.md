Week 01 - Cybersecurity Lab Setup

**Networkwalks Cybersecurity Internship — Batch B083**

Project Overview

This project involved setting up a practical cybersecurity laboratory environment using **Oracle VirtualBox** and **Kali Linux**.

The laboratory provides an isolated environment for practicing networking, cybersecurity, ethical hacking, and future security testing activities.

The setup was completed according to the Week 01 lab requirements provided by Networkwalks.

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
- Document the laboratory configuration and troubleshooting process.

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

1. VirtualBox NAT Network Configuration

A custom VirtualBox NAT Network named **`NatNetwork`** was configured for the cybersecurity laboratory.

The network was configured with:

- Network: `10.0.0.0/24`
- Gateway: `10.0.0.1`
- DHCP: Disabled
- IPv6: Disabled

DHCP was disabled so that Kali Linux could use the required static address:

`10.0.0.2/24`

2. Kali Linux Network Configuration

The Kali Linux virtual machine was connected to the custom `NatNetwork`.

The network connection was configured using **NetworkManager**.

The following configuration was applied:

- IP Address: `10.0.0.2/24`
- Gateway: `10.0.0.1`
- DNS: `8.8.8.8`, `1.1.1.1`
- Connection: `Wired connection 1`
- Interface: `eth0`

The configuration was verified successfully before activating the network connection.

3. Network Verification

After configuring the network, connectivity was tested from Kali Linux.

Gateway Test

```bash
ping -c 3 10.0.0.1
```

The gateway responded successfully with no packet loss during the verification test.

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

4. Clipboard and Drag-and-Drop

VirtualBox integration features were enabled for the Kali Linux virtual machine.

The following features were configured:

- Shared Clipboard: **Bidirectional**
- Drag and Drop: **Bidirectional**

Both features were tested and confirmed to be working.

These features improve interaction between the Windows host and Kali Linux virtual machine during laboratory activities.

5. Shared Folder Configuration

A shared folder was configured between the Windows host and Kali Linux.

Windows Host

```text
C:\downloads
```

Kali Linux

```text
/media/sf_downloads
```

A convenient `/downloads` path was also created in Kali Linux as a symbolic link to the VirtualBox shared folder.

The shared folder was tested by creating a text file on the Windows host and reading its contents successfully from Kali Linux.

The test was performed using:

```bash
cat /downloads/test.txt
```

The file contents were successfully displayed in Kali Linux.

6. VM Snapshot

After completing the laboratory configuration, a clean snapshot of the Kali Linux virtual machine was created.

Snapshot Name

```text
Week1 - Clean Lab Setup
```

The snapshot preserves the configured state of the laboratory and provides a clean recovery point for future cybersecurity exercises.

7. Troubleshooting

During the static IP configuration, Kali Linux initially failed to activate the required `10.0.0.2/24` configuration.

The VirtualBox NAT Network configuration was checked and the Kali Linux network connection was reviewed before troubleshooting the activation problem.

Following the troubleshooting guidance provided by Networkwalks, the following NetworkManager setting was applied:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

The network connection was then restarted:

```bash
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

After applying the configuration, the connection activated successfully and Kali Linux operated with the required `10.0.0.2/24` address.

Troubleshooting Process

The troubleshooting process involved:

1. Checking the VirtualBox NAT Network configuration.
2. Verifying the Kali Linux network connection settings.
3. Investigating the static IP activation failure.
4. Applying the recommended NetworkManager adjustment.
5. Restarting the network connection.
6. Re-testing the network configuration.
7. Confirming that the required static IP configuration was operational.

Troubleshooting Lesson

This issue provided practical experience in diagnosing Linux network configuration problems.

The experience reinforced the importance of systematically checking network configuration, understanding NetworkManager behavior, and testing changes before moving forward.

8. Challenges Encountered

The main challenge during the lab setup was activating the required static IP address on the Kali Linux virtual machine.

The issue was resolved by applying the NetworkManager Duplicate Address Detection (DAD) workaround recommended in the Networkwalks lab documentation.

This provided practical experience in:

- Linux network configuration
- NetworkManager
- Static IP addressing
- VirtualBox NAT Network configuration
- Network troubleshooting
- Connectivity verification

9. Evidence

Screenshots documenting the completed laboratory setup are maintained in the `screenshots/` directory.

The evidence includes:

1. Kali Linux network configuration
2. VirtualBox NAT Network configuration
3. Shared folder configuration
4. Shared folder functionality test
5. Kali Linux VM snapshot

Evidence Files

```text
screenshots/
├── 01-kali-network-configuration.png
├── 02-virtualbox-natnetwork.png
├── 03-shared-folder-configuration.png
├── 04-kali-shared-folder-test.png
└── 05-week1-kali-snapshot.png
```

10. Learning Outcomes

By completing this laboratory, I gained practical experience in:

- Virtual machine deployment and configuration
- Oracle VirtualBox
- NAT Network configuration
- Linux network configuration
- Static IP addressing
- Gateway configuration
- Internet connectivity testing
- DNS resolution
- NetworkManager
- VirtualBox integration features
- Host-to-VM shared folders
- Linux network troubleshooting
- Virtual machine snapshots
- Technical documentation

The exercise also reinforced the importance of understanding networking fundamentals as a foundation for cybersecurity work.

11. Lab Status

**Status: Completed**

The required Week 01 cybersecurity laboratory environment has been successfully configured and tested.

The Kali Linux virtual machine has:

- A working static network configuration
- Gateway connectivity
- Internet connectivity
- DNS resolution
- Host-to-VM file sharing
- VirtualBox integration features
- A clean recovery snapshot

12. Future Work

The Networkwalks laboratory documentation identifies additional virtual machines and inter-machine ping testing as Phase 2 activities.

These activities are considered future or optional work for the current laboratory setup.

Future exercises may expand the laboratory with additional virtual machines for:

- Network security practice
- Ethical hacking exercises
- Penetration testing
- Capture The Flag (CTF) activities
- Security testing in controlled laboratory environments

Conclusion

The Week 01 cybersecurity laboratory was successfully established using Oracle VirtualBox and Kali Linux.

The completed environment provides a practical foundation for future networking, cybersecurity, ethical hacking, and security testing exercises.

The project also provided valuable hands-on experience with virtualized environments, static network configuration, connectivity testing, shared resources, and Linux network troubleshooting.


**Networkwalks Academy — Cybersecurity Internship**  
**Batch B083 | Week 01**  
**Practical Lab: Cybersecurity Lab Setup**
