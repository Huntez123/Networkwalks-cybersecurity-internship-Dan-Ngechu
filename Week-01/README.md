Week 01 — Cybersecurity Lab Setup
Project
Setup of a cybersecurity testing lab environment using Oracle VirtualBox and Kali Linux.

Objectives
- Set up Oracle VirtualBox
- Configure a custom NAT Network
- Configure Kali Linux as the attacking/hacker machine
- Configure the lab network using the `10.0.0.0/24` subnet
- Assign Kali Linux the IP address `10.0.0.2/24`
- Enable Internet connectivity
- Enable clipboard and file drag-and-drop
- Configure a shared `/downloads` folder
- Create a clean VM snapshot

Lab Environment
| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Attacking Machine | Kali Linux |
| Network Type | NAT Network |
| Network | `10.0.0.0/24` |
| Kali IP | `10.0.0.2/24` |
| Gateway | `10.0.0.1` |
| Shared Folder | `/downloads` |

Status
✅ Week 01 Lab Setup Completed

Evidence
Screenshots documenting the configuration and testing of the lab environment are stored in the `screenshots` directory.

Troubleshooting
During the Kali network configuration, the instructor's recommended NetworkManager DAD workaround was used:

`ipv4.dad-timeout 0`

This allowed the Kali VM to successfully activate the `10.0.0.2/24` configuration.

## Next Steps

Continue with the next Networkwalks Academy cybersecurity internship task.
