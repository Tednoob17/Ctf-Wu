## Introduction to Active Directory

- Tier 0
- Fundamental 
- General
- 16 Sections
- 10 cubes
- 7 hours


### Why Active Directory
Active Directory (AD) is a directory service for Windows network environments. It is a distributed, hierarchical structure 
that allows for centralized management of an organization's resources, including users, computers, groups, network devices,
file shares, group policies, devices, and trusts. AD provides authentication and authorization functions within a Windows domain environment. 
It has come under increasing attack in recent years. It is designed to be backward-compatible, and many features are arguably not
"secure by default," and it can be easily misconfigured. This weakness can be leveraged to move laterally and vertically 
within a network and gain unauthorized access. AD is essentially a sizeable read-only database accessible to all users within the domain, 
regardless of their privilege level. A basic AD user account with no added privileges can enumerate most objects within AD. 
This fact makes it extremely important to properly secure an AD implementation because ANY user account, 
regardless of their privilege level, can be used to enumerate the domain and hunt for misconfigurations and flaws thoroughly. Also, multiple attacks can be performed with only a standard domain user account, showing the importance of a defense-in-depth strategy and careful planning focusing on security and hardening AD, network segmentation, and least privilege. 
One example is the [noPac attack](https://www.secureworks.com/blog/nopac-a-tale-of-two-vulnerabilities-that-could-end-in-ransomware) that was first released in December of 2021.

Active Directory makes information easy to find and use for administrators and users. AD is highly scalable, supports millions 
of objects per domain, and allows the creation of additional domains as an organization grows.

## Info

- defense-in-depth strategy (Defense in depth is a strategy that leverages multiple security measures to protect an organization's assets. The thinking is that if one line of defense is compromised, additional layers exist as a backup to ensure that threats are stopped along the way.)


![whyad1](./img/whyad1.png)
