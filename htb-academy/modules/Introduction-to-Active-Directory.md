## Introduction to Active Directory

- Tier 0
- Fundamental 
- General
- 16 Sections
- 10 cubes
- 7 hours


## Why Active Directory
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

### Info

- defense-in-depth strategy (Defense in depth is a strategy that leverages multiple security measures to protect an organization's assets. The thinking is that if one line of defense is compromised, additional layers exist as a backup to ensure that threats are stopped along the way.)


![whyad1](./img/whyad1.png)

It is estimated that around 95% of Fortune 500 companies run Active Directory, making AD a key focus for attackers. A successful attack such as a phish that lands an attacker within the AD environment as a standard domain user would give them enough access to begin mapping out the domain and looking for avenues of attack. As security professionals, we will encounter AD environments of all sizes throughout our careers. It is essential to understand the structure and function of AD to become better informed as both an attacker and a defender.

Ransomware operators have been increasingly targeting Active Directory as a key part of their attack paths. [The Conti Ransomware](https://www.cisa.gov/sites/default/files/publications/AA21-265A-Conti_Ransomware_TLP_WHITE.pdf) which has been used in more than 400 attacks around the world has been shown to leverage recent critical Active Directory flaws such as [PrintNightmare (CVE-2021-34527)](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-34527) and [Zerologon (CVE-2020-1472)](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2020-1472) to escalate privileges and move laterally in a target network. 

Understanding the structure and function of Active Directory is the first step in a career path to find and prevent these types of flaws before attackers do. Researchers are continually finding new, extremely high-risk attacks that affect Active Directory environments that often require no more than a standard domain user to obtain complete administrative control over the entire domain. There are many great open-source tools for penetration testers to enumerate and attack Active Directory. Still, to use these most effectively, we must understand how Active Directory works to identify obvious and nuanced flaws. Tools are only as effective as their operator is knowledgeable. So let's take the time to understand the structure and function of Active Directory before moving into later modules that will focus on in-depth manual and tool-based enumeration, attacks, lateral movement, post-exploitation, and persistence.

This module will lay the foundations for starting down the path of enumerating and attacking Active Directory. We will cover, in-depth, the structure and function of AD, discuss the various AD objects, discuss user rights and privileges, tools, and processes for managing AD, and even walk through examples of setting up a small AD environment.



## History of Active Directory

LDAP, the foundation of Active Directory, was first introduced in RFCs as early as 1971. Active Directory was predated by the X.500 organizational unit concept, which was the earliest version of all directory systems created by Novell and Lotus and released in 1993 as Novell Directory Services.

Active Directory was first introduced in the mid-'90s but did not become part of the Windows operating system until the release of Windows Server 2000. Microsoft first attempted to provide directory services in 1990 with the release of Windows NT 3.0. This operating system combined features of the [LAN](https://en.wikipedia.org/wiki/LAN_Manager) Manager protocol and the [OS/2](https://en.wikipedia.org/wiki/OS/2) operating systems, which Microsoft created initially along with IBM lead by [Ed Iacobucci](https://en.wikipedia.org/wiki/Ed_Iacobucci) who also led the design of [IBM DOS](https://en.wikipedia.org/wiki/IBM_PC_DOS) and later co-founded Citrix Systems. The NT operating system evolved throughout the 90s, adapting protocols such as LDAP and Kerberos with Microsoft's proprietary elements. The first beta release of Active Directory was in 1997.

The release of Windows Server 2003 saw extended functionality and improved administration and added the **Forest** feature, which allows sysadmins to create "containers" of separate domains, users, computers, and other objects all under the same umbrella. Active [Directory Federation Services (ADFS)](https://en.wikipedia.org/wiki/Active_Directory_Federation_Services) was introduced in Server 2008 to provide Single Sign-On (SSO) to systems and applications for users on Windows Server operating systems. ADFS made it simpler and more streamlined for users to sign into applications and systems, not on their same LAN.

### Info

- LDAP :The Lightweight Directory Access Protocol (LDAP /ˈɛldæp/) is an open, vendor-neutral, industry standard application protocol for accessing and maintaining distributed directory information services over an Internet Protocol (IP) network.|st à l'origine un protocole permettant l'interrogation et la modification des services d'annuaire (il est une évolution du protocole DAP).

- ADFS :Active Directory Federation Services (AD FS), a software component developed by Microsoft, can run on Windows Server operating systems to provide users with single sign-on access to systems and applications located across organizational boundaries. |Active Directory Federation Services est un composant de Windows Server pouvant être installé sur les serveurs Windows afin de faciliter l'accès aux utilisateurs, aux systèmes et applications.

- OS/2 :OS/2 (Operating System/2) is a series of computer operating systems, initially created by Microsoft and IBM under the leadership of IBM software designer Ed Iacobucci. As a result of a feud between the two companies over how to position OS/2 relative to Microsoft's new Windows 3.1 operating environment, the two companies severed the relationship in 1992 and OS/2 development fell to IBM exclusively.

- IBM DOS : Developed by Microsoft, it was also sold by that company as MS-DOS. Both operating systems were identical or almost identical until 1993, when IBM began selling PC DOS 6.1 with new features.

- RFC :  is a publication in a series from the principal technical development and standards-setting bodies for the Internet, most prominently the Internet Engineering Task Force (IETF).

- X.500: X.500 is a series of computer networking standards covering electronic directory services. The X.500 series was developed by the Telecommunication Standardization Sector of the International Telecommunication Union (ITU-T).

