# Risk Assessment Project 2

## 1. Current Network Model

### 1a. Network Model
- We will have a model like the following image below:
![image](https://github.com/hoangbui24/Risk-Assessment-Project-2/assets/71567852/776ef8b5-cac8-44c8-a63e-0e31eb4d187b)
> In the image, the two cloud-shaped fields are the smaller branches of business in Ho Chi Minh City (above) and in Ha Noi Capital (below).

### 1b. Dive deeper about model
- ABC Company has its headquarters located in Ho Chi Minh with 100 users and another large branch located in Hanoi with about 50 users. In addition, in Ho Chi Minh and Hanoi, the company also has small branches (about 15 small branches in HCM, about 20 small branches in Hanoi). Each branch ranges from 3 to 10 people.
  
- System details:
  - Business's devices list is described as the following table <br>

Numberical Order | Devices | Quantity | Location | Serial Number | 
--- | --- | --- | --- |--- |
1 | Server HP DL 380G5 (Domain - Email) | 1 | HCM | 1 | 
2 | Server HP DL 380G5 (File) | 1 | HCM | 2 |
3 | Server HP DL 380G5 (Application) | 1 | HCM | 3 | 
4 | NAS Thecus N8810U-G (Storage) | 1 | HCM | 4 | 
5 | Core switch 3850G 24 port | 1 | HCM |5 |
6 | Access switch 2960 PoE 48 port | 4 | HCM | 6 |
7 | HP Color LaserJet Pro MFP M476nw | 2 | HCM | 7 | 
8 | HP LaserJet Enterprise Flow MFP M630z | 1 | HCM | 8 |
9 | Wireless N Access Point TL-WA801ND | 5 | HCM | 9 |
10 | Modem ADSL Draytek 3200 | 1 | HCM | 10 | 
11 | Server HP DL 380G5 (Domain) | 1 | HN | 11 |
12 | Server HP DL 380G5 (File) | 1 | HN | 12 |
13 | Server HP DL 380G5 (Application) | 1 | HN | 13 | 
14 | NAS Thecus N8810U-G (Storage) | 1 | HN | 14 |
15 | Core switch 3850G 24 port | 1 | HN | 15 |
16 | Access switch 2960 PoE 48 port | 4 | HN | 16 | 
17 | HP Color LaserJet Pro MFP M476nw | 2 | HN | 17 |
18 | HP LaserJet Enterprise Flow MFP M630z | 1 | HN | 18 |
19 | Wireless N Access Point TL-WA801ND | 5 | HN | 19 | 
20 | Modem ADSL Draytek 2900 - Firewall | 1 | HN | 20 |
21 | Access switch 2960 PoE 24 port | 1 | Each branch | 21 |
22 | HP LASERJET PRO 400 PRINTER M401N | 1 | Each branch | 22 |
23 | VIGOR 2830 | 1 | Each branch | 23 |

- Business's applications list is described as the following table <br>

Numberical Order | Application |
--- | --- | 
1 | Domain – Wink2k3 | 
2 | Exchange Email 2007 – Win2k3 | 
3 | File – Win2k3 | 
4 | Accounting Application | 
5 | Client – Win7 | 
6 | MS Office | 
7 | Other popular software: Skype, Adobe, Unikey, Dropbox, Yahoo, Browser (IE, Firefox, Chrome),... | 


## 2. System operating procedures
- Currently in the enterprise there is no document regulating the regulations and operating procedures of the system. However, the operating characteristics of the system can be listed as follows:
  - All servers running HDH: Windows Server 2003
  - All clients running HDH: Windows 7
  - Domain service: a Primary Domain server running at HCM headquarters and a Secondary Domain server running in Hanoi
  - Email service: exchange 2007 server, all clients at all headquarters and branches will connect here to send and receive emails
  - File service: in the system there are 2 distributed file servers in HCM and Hanoi. Data runs independently with no parallel mechanism to back up each other.
  - Printing service: client connects directly to the Printer for printing
  - Firewall: use Vigor modem to act as a firewall to protect the system
  - Special application: accounting software
  - Client's internet connection process: client accesses the internet directly at the headquarters or branch. Clients at the southern branches will access data to the File in HCM
and clients at the Northern and Central branches will access data to the File in Hanoi.
  - Data backup and recovery process: use Windows Backup to backup data, backup data will be saved in Storage
  - Access process to Data Center: use key to enter. Head of IT department manages keys.
  - The process of connecting to the internal network uses a network cable: the client attaches the network cable and accesses normally, there is no control mechanism
  - Process of connecting to the internal network using a wireless network: the client accesses the wifi network using the Key. When accessing, the client can access the server area. Because the network system is a flat network, there is no VLAN division.

## 3. Assessment

### 3a. Analyze the availability of services in the system (Domain, File and Email) and the availability of network infrastructure

> [!NOTE]
> Based on the Availability Management Report template at https://www.itsm-docs.com/blogs/itil concepts/availability-management-report

- Checklist for Availability report
#### Domain

| Details of availability  | Agreed availability  | Measured availability | Availability targets |
--- | --- | --- | --- |
| Domain service system is available 24/7  | Able to manage accounts of up to 350 employees  | ~ 200 staff accounts | Ability to expand up to 400 accounts by next year |

| | |
--- | --- |
| Incident Description | - Domain server at Ho Chi Minh City branch is overloaded (-1%)<br> - Domain system attacked by malware leading to data loss (-1%)<br> - Domain system attacked by cyber attack resulting in system unresponsiveness (-1%)<br> - Domain server is broken (-1%) |

| Incident type  | Cause  | Response for eliminating the failure  | Measures for avoiding failures  |
--- | --- | --- | --- |
| System overload | Domain service is shared with Email service on the same server | Separate email service and Domain service into 2 servers | 
| Data loss | Malware, Wink2k3 Operating System version vulnerability | - Install AV programs and investigate system data<br> - Upgrade the operating system and server version | 
| The system is not responding | Cyber attack | Use specialized firewalls and IPS | 
| Server broken | Physical/external factors | - Add 1 Additional domain server per branch<br> - There is a data backup mechanism |

#### File
    
| Details of availability  | Agreed availability  | Measured availability  | Availability targets  |
--- | --- | --- | --- |
File service system is available 24/7 | Able to store and access 100% of company data | Able to store and access 95% of company data | Potential for expansion up to 200% through next year |

| | |
--- | --- |
| Incident Description | - File server system attacked by malware leading to data loss (-1%)<br> - The File server system was damaged by a cyber attack, causing the system to become unresponsive (-1%)<br> - Server File server is broken (-1%) |

| Incident type  | Cause  | Response for eliminating the failure  | Measures for avoiding failures  |
--- | --- | --- | --- |
| Data loss | Malware, Wink2k3 Operating System version vulnerability | - Install AV programs and investigate system data<br> - Upgrade the operating system and server version | 
| The system is not responding | Cyber attack | Use specialized firewalls and IPS | 
| Server broken | Physical/external factors | - There is a mechanism to backup data to tape and a data recovery center<br> - Add 2 File servers with a mechanism to run in parallel and synchronize data of the 2 servers |

#### Email

| Details of availability  | Agreed availability  | Measured availability  | Availability targets  |
--- | --- | --- | --- |
Email service system is available 24/24 | Able to process and navigate mail with low latency | Able to process and navigate mail with unstable status | Scalable to handle more emails |

| | |
--- | --- |
| Incident Description | - Email service system attacked by malware leading to loss of important data (-1%)<br> - The Email service system was sabotaged by a cyber attack, resulting in the system becoming unresponsive (-1%)<br> - Email service system is overloaded (-1%)<br> - Email service server is broken (-1%) |

| Incident type  | Cause  | Response for eliminating the failure  | Measures for avoiding failures  |
--- | --- | --- | --- |
| Data loss | Malware, vulnerabilities on Exchange Email 2007 version | - Install AV drivers and investigate system data<br> - Upgrade server operating system, Exchange version | 
| The system is not responding | Cyber attack | Use specialized firewalls and IPS | 
| System overload | - Domain service is shared with Email service on the same server<br> - The number of emails is too large | - Separate email service and Domain service into 2 servers<br> - Enhanced 1 email server at Hanoi branch, with synchronization mechanism with Ho Chi Minh City branch |
| Server broken | Physical/external factors | - There is a data backup mechanism |

#### Network Infrastructure

| Details of availability  | Agreed availability  | Measured availability  | Availability targets  |
--- | --- | --- | --- |
The wired network system is available 24/24 | Capable of high-speed, uninterrupted transmission between devices | There is a possibility of transmission between devices with delay | Able to expand network speed for the system |
The wireless network system is available 24/7 | Capable of high-speed transmission | Capable of medium speed transmission | Able to expand network speed for the system |

| | |
--- | --- |
| Incident Description | - The network system was damaged by a cyber attack, causing the system to become unresponsive (-1%)<br> - The network system is overloaded/congested at the Data center (-1%)<br> - Site2site VPN network speed is unstable between 2 Data centers (-1%)<br> - Router/switch/network cable is damaged (-1%) |

| Incident type  | Cause  | Response for eliminating the failure  | Measures for avoiding failures  |
--- | --- | --- | --- |
| Network overload/congestion | Large data access from branches, intranet and wireless network | - Enhance network lines<br> - Use Load balancing devices at each Data center | 
| The system is not responding | Cyber attack | Use specialized firewalls and IPS | 
| Network speed is unstable | - The data exchange is too large | - Enhance network lines |
| Device broken | Physical/external factors | - Increase additional equipment and backup network lines<br> - There is a routing mechanism to the backup network when a problem occurs |

#### Service Downtime

| Service | Details | Agreed service ontime (%) | Dowtime (%) | Availability (%) |
--- | --- | --- | --- | --- |
| Domain | Domain service system is available 24/7 | 100 | 4 | 96 |
| File | File service system is available 24/7 | 100 | 3 | 97 |
| Email | Email service system is available 24/24 | 100 | 4 | 96 |
| Network Infrastructure | The network system is available 24/7 | 100 | 4 | 96 |


### 3b. Analyze risks leading to information loss caused by users
- Accidentally deleting, overwriting, or modifying data: Incorrect actions on the part of the user can sometimes misplace, overwrite, or even delete data.
- Loss or damage of storage devices: Network users at businesses can lose or damage data storage devices such as USBs, TAPEs, CDs, etc.
- Downloading malicious files of unknown origin: Downloading malicious files of unknown origin, despite warnings from the firewall, can "piggyback and bite the chickens" when activating an executable file containing malicious code. leading to data loss.
- Error due to corruption: Company data can be sold by users, email service information can be shared, or printers do not have a protection mechanism, users can extract information from there and sell it.

### 3c. Analyze the risks of system attacks
- Hackers attack and invade: First, in terms of systems, we can see Server running version 2003, users running Windows 7, Email using Exchange 2007,... We can see that all of the above systems are under Old versions have a lot of security holes, for example the Eternal Blue vulnerability on Windows 7. In addition, the process of connecting to the internal network using network cables has no control mechanism, this can be a source for attackers to steal data.
- DDoS: DDoS attacks are always the most popular and destructive attack method. We can see that the system does not have a load balancing method. Therefore, you can easily get hit with a DDoS attack.
- Physical attack: An attacker can physically attack such as stealing equipment or breaking into the Data Center when there are no basic defense methods in place.
- Social attacks: The system can be attacked by Social Engineering, because there is no information security operating policy, so employees' awareness of security issues is not really high, attackers can can trick users using Phishing methods to steal data.
- Impact from nature: The fact that the Data Center does not have measures or specialized equipment to protect it, as well as no information about database standards, is also a possible risk. occurs when there are natural disasters or unexpected natural factors.
  
### 3d. Analyze risks in the data backup and recovery process
- Incomplete backup: With Windows Backup's limited memory (about 2T), long-term use is almost impossible.
- Data loss: Windows Backup has a mechanism that automatically deletes older data to create space for newer data.
- Windows Backup only supports storing data on local drives, or remote shared folders, so when something goes wrong or needs to move a large amount of data, it will not support backing up to tapes. We can only save one backup. Although we can send the backup to a network share, it is useless. All backups will be automatically deleted when the new backup is complete.
- Not having a clear control mechanism and data backup and recovery policy is also a big risk, because when an incident occurs, response will not be timely.
- There is no cloud service provided yet, making backup and recovery more difficult, since there are only 2 Domains.

### 3e. Risk score table
- The risk score is assessed in the table below
> For a better view, please visit [Google Sheet](https://docs.google.com/spreadsheets/d/1-c5VqQTY-Y9FefWBAZWi0TkA1_KWZdzRHcZbHIpYRCo/edit?usp=sharing)

![image](https://github.com/hoangbui24/Risk-Assessment-Project-2/assets/71567852/4716d0db-6d37-44d4-85b3-e5bf72363ebb)

### 3e. Propose solutions to limit these risks
- Risks leading to loss of information caused by users:
  - Train users on safe computer and network use
  - Use security solutions such as anti-virus software, firewalls,...
  - Use data storage devices that are shockproof and anti-lost
- Risks of system attacks:
  - Use security solutions such as firewalls, VPN,...
  - Update software regularly
  - Make it a habit to use strong passwords and change them periodically
- Risks in the data backup and recovery process:
  - Develop and implement a complete and strict data backup and recovery process
  - Back up data regularly and fully
  - Store backup data in a safe location

![image](https://github.com/hoangbui24/Risk-Assessment-Project-2/assets/71567852/8d5f32f2-622d-4085-baae-1ca3e210b851)
  - Veritas Backup Exec is a fast, cost-effective, and unified data backup and recovery solution for data protection. Whether they are stored anywhere from virtual machines, physical machines to the cloud. Veritas Backup Exec helps you proactively manage everything. You can choose what to back up, where to store it, and choose payment methods. Your data is always safe and ready to use. Easily back up on-premise data to the cloud, protect cloud workloads, restore data from the cloud, or just connect data to on-premise storage.


