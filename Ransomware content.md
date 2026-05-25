# What is Ransomware?
In simple terms, ransomware is a type of malicious software (malware) that, Locks your files or computer system and demands money (a ransom typically in cryptocurrency) to unlock it.

Think of it like this, Imagine someone breaks into your house, puts all your important documents into a locked box, takeaway that box with him and leaves a note that says:

“Pay me $1,000 or you’ll never see your files again.”

That’s what ransomware does—but digitally.

## What it typically does:

- Infects your computer (often through a fake email or malicious website).
- Encrypts your files—making them unreadable.
- Shows a ransom note demanding payment (usually in cryptocurrency like Bitcoin).
- Sometimes also steals your files and threatens to leak them if you don’t pay (this is called double extortion).

Money is not the only motivation, sometimes cheating, spying and disrupting operations can also be consider as motivations. For example, recently before and during Russia’s war against Ukraine, some ransomware attacks have been triggered by both sides.

## Two Different Models

In human-operated ransomware attack model, a group of hackers personally breaks into a company’s network. They don’t just hit “go” and walk away—they:

- Study the company first to find weak spots (like old software or exposed accounts)
- Sometimes even look at the company’s financial documents to figure out how much ransom to demand
- Only after all that, they install the ransomware and lock the files
- Think of it like burglars who watch a building, learn the security system, and plan carefully before breaking in.

A ransomware-as-a-service attack model works like renting out a ransomware toolkit.

- One group of cybercriminals builds the ransomware (the developers)
- Another group—called affiliates—uses it to attack companies
- When a company pays the ransom, they split the money
- It’s like someone building a lock-picking tool and letting others use it for a fee—and they both share the loot.

The process of ransomeware attack: 

1. The ransomware developer creates a specific exploit to be afterwards shared with an affiliate.

2. The affiliate updates the exploit code to the hosting site and,

3. Selects the target victim as well as the attack vector to deliver the exploitation (email, web, etc.).

4. The victim bites the trap so that,

5. The ransomware is downloaded and installed.

6. The ransomware will communicate with the command and control (C&C) server to get the ciphering key and, apart from ciphering the victim’s files.

7. It can perform lateral movements to identify other potential targets, make itself persistent, delete file backups and hide its presence.

8. The extortion message is shown to the victim, as is the way to pay.

9. Another malicious agent is potentially in charge of money laundering such that it would be difficult to identify both the ransomware developer and affiliate.

10. The affiliate can decide to send the ciphering key to the victim or not in order to get additional payments.
<img width="550" height="509" alt="image" src="https://github.com/user-attachments/assets/78c2d5fc-493f-47e4-8e43-574d5811e0b6" />

## Types of Ransomware
### Crypto Ransomware

- In a crypto ransomware attack, the attacker encrypts a victim’s sensitive data or files so that they can’t access them unless they pay a requested ransom. In theory, once the victim pays, the attacker turns over a decryption key that gives them access to the files or data, however, there’s no guarantee. Many organisations have permanently lost access to their files even after paying the ransom.
- Most ransomware uses a combination of symmetric and asymmetric encryption algorithms. Symmetric encryption is highly efficient for bulk encryption. Ransomware uses it to encrypt files and deny their owners access to them. Asymmetric encryption is used to protect the symmetric encryption keys. If the public key is bundled with the malware, the ransomware can encrypt and store the symmetric encryption key alongside the encrypted files. The attackers keep only copy of the private key and can use it to decrypt the symmetric key once the victim has paid the ransom.
- Ransomware’s encryption process has also evolved. For example, some ransomware variants will only encrypt part of a file. This enables the encryption process to occur more quickly — decreasing the risk of interruption — while still rendering the files unusable.

### 7 Stages of Crypto Ransomware:

#### 1. Reconnaissance

Attackers study the target organization to identify weaknesses. For example, Hackers search LinkedIn to find employees in the finance department, then scan the company’s external servers to spot an exposed Remote Desktop port.

#### 2. Weaponization

The attackers build or prepare a ransomware payload designed to exploit what they found. Attackers craft a fake invoice email attachment that looks like a PDF but contains embedded ransomware. It’s disguised so antivirus won’t catch it.

#### 3. Delivery

The malicious file or link is sent to the target—often by email or fake website. We can think of it as, An HR employee receives an email: “Your benefits statement is attached.” They open the file—thinking it's legit.

**Common methods:**

- Phishing emails
- Malvertising
- USB drops
- Compromised websites

#### 4. Exploitation

The victim triggers the malware—intentionally or unknowingly. From the above HR example, When the HR employee opens the fake PDF, a hidden macro runs in the background and starts installing malware.

#### 5. Installation

The ransomware is now installed on the system. The malware installs itself in a hidden system folder, disables antivirus, and prepares to encrypt files.

**What could happen here:**

- File system scanning
- Persistence mechanisms (like modifying registry or scheduled tasks)
- Dropping encryption modules

#### 6. Command & Control (C2)

The infected system contacts the attacker’s server to get instructions or encryption keys. The malware sends device info to a server in another country, then downloads a unique encryption key to begin locking files.

**Why it matters:**

- Helps attacker control the malware
- Enables exfiltration of sensitive data
- Used to receive payment instructions or even auto-update the ransomware

#### 7. Actions (on Objectives)

The actual attack phase—encrypting files, deleting backups, showing the ransom note. All company documents, HR files, and financial records are renamed with .locked. A message appears:
“Your files are encrypted. Pay 2 BTC within 72 hours or lose them forever.”

**Includes:**

- File encryption
- Shadow copy deletion (vssadmin delete shadows)
- Data exfiltration
- Ransom note delivery
- System-wide spread
<img width="550" height="811" alt="image" src="https://github.com/user-attachments/assets/e8d79894-dc18-4519-b51c-e0973ae42b2f" />
- Example: Petya/NotPetya, WannaCry

### Locker Ransomware

Locker ransomware is a type of malware that locks your entire device, not just your files. It stops you from using your computer or phone until you pay a ransom.

It usually sneaks in through:

- Malicious ads (called malvertising)
- Fake apps or files (like a trojan pretending to be something useful)

Once inside, it blocks access in one of these ways:

**- Full-Screen Fake Lock**
  - It shows a full-screen message that looks like your device is locked.
  - You can’t see the taskbar, move the mouse, or use shortcuts.
**- Changing Your Login Password**
  - It may change your PIN or password, locking you out for real.
  - Sometimes it disables system settings so you can’t fix it easily.

**How Is It Different from Crypto Ransomware?**
- Locker ransomware locks your screen or device.
- Crypto ransomware locks your files by encrypting them. Crypto ransomware is more common these days.

**Examples of Locker Ransomware**

- WinLock – One of the earliest known lockers in Russia
- Reveton – Pretended to be a police warning
- LockerPin – Locked Android phones by changing the PIN
<img width="795" height="460" alt="image" src="https://github.com/user-attachments/assets/58dab4c2-c55b-4a04-91c1-9144c905ea3a" />


### Scareware (Fake Antivirus)

Scareware is a type of fake software or scam that tries to scare you into paying money.

How It Works

- It shows a scary message—like “Your computer is infected!” or “You broke the law!”
- It might pretend to be from the police or FBI, accusing you of doing something wrong
- Then it says: “Pay a fine to fix it or avoid punishment”

The cybercriminals want you to panic and pay a fake “ransom” or fine, even though nothing is really wrong with your computer.

For example: A message pops up:
“You’ve been caught viewing illegal content. Your computer is locked. Pay $300 to avoid arrest.”
(But it’s all fake!)
<img width="516" height="383" alt="image" src="https://github.com/user-attachments/assets/fecdcb06-d5c4-4c5b-90b3-59f1e677f181" />


### Leakware / Doxware

- Threatens to publicly release sensitive data unless ransom paid—data exfiltration used as extortion leverage.
- Leakware places additional pressure on the victim, who may fear damage to reputation or business opportunities if certain information is made public.
- Increasingly used by human-operated ransomware groups.

#### Why It’s So Dangerous

- It creates extra pressure to pay—not just to unlock your files, but to protect your reputation
- Victims may worry about:
  - Losing customer trust
  - Legal trouble (e.g., data protection violations)
  - Business deals being exposed

Summary Table 
--------------+------------------------------+------------------------------+
Type          |  Mechanism                   |  Example & Impact
--------------+------------------------------+------------------------------+
Crypto        |  File/sys encryption         |  WannaCry (EternalBlue worm)
Locker        |  Full system lock            |  WinLock, Reveton
Scareware     |  Fake alerts, no encryption  |  Fake antivirus pop-ups
Leakware      |  Data theft + publish threat |  Leak-based extortion gangs


## How Can Ransomware Exploited
**Phishing & Social Engineering**
Phishing is the most common ransomware delivery method, where users are tricked into clicking malicious links or downloading infected attachments. Spear phishing is more targeted—attackers research the victim and impersonate a trusted contact (like IT staff or suppliers). 

For example, The Conti ransomware gang sent personalised emails to hospital staff, pretending to be IT. When someone clicked, attackers got access and locked down hospital systems.

**Malware Delivery (Malvertising / Drive-by)**
Malvertising refers to injecting malicious code into legitimate ad networks, which can redirect victims to exploit kits that silently install ransomware. Even reputable sites may unknowingly serve these ads. Drive-by downloads exploit browser/plugin vulnerabilities—users don’t need to click anything.

**RDP/SSH Brute‑Force or Credential Theft**
Unsecured Remote Desktop Protocol (RDP) or SSH endpoints exposed to the internet are frequent entry points. Attackers scan IP ranges, then brute-force credentials using leaked username-password combos or password spraying. Once inside, attackers deploy ransomware manually.

For example, An exposed RDP server with a weak password like “Welcome123” becomes the entry point. Minutes later, the network is encrypted.

**Zero‑Day Exploits**
A zero-day is a flaw in software that nobody knows about yet—not even the company that made it. Threat actors exploit it before the vendor is aware, giving defenders no time to patch. Zero-days are powerful because even fully updated systems can be vulnerable.

 

## Ways to Exfiltrate Data
-------------------+-----------+----------------------+---------------------+
Technique          |  Protocol |  Visibility          |  Example Group/Tool
-------------------+-----------+----------------------+---------------------+
HTTPS Upload       |  HTTPS    |  Medium (Encrypted)  |  BlackByte, Clop
DNS Tunneling      |  DNS      |  Very Low            |  APT32, RaaS variants
FTP/SFTP           |  FTP/SFTP |  Medium              |  DarkSide
Email SMTP         |  SMTP     |  High (Alertable)    |  EvilCorp
SMB over VPN       |  SMB      |  Low (Internal)      |  FIN11
Reverse Shell      |  TCP      |  Medium              |  Ryuk, TA505
Custom Exfil Tool  |  Mixed    |  Low                 |  StealBit, ExMatter
Tor Hidden Service |  Tor      |  Very Low            |  REvil, BlackMatter

## Case Study: Marks & Spencer
**How it happened?**

- Exploited human trust.
- Attack began around April 2025, Attackers impersonated an authorised person and social-engineered an IT service desk (reportedly a third-party contractor’s help desk) into resetting credentials and disabling multi-factor authentication, giving the hackers their foothold in the network.
- extracted the Windows domain controller’s NTDS.dit
- The breach was carried out by Scattered Spider in alliance with the DragonForce ransomware operation.

**consequences**

- Systems encrypted; warehouse logistics and contactless payments disrupted; online and app ordering offline.
- Financial impact: ~£300 million hit to operating profits and over £750 million lost in market capitalization.
- Data potentially compromised: up to 10 million customer records and internal HR files; M&S stated payment data likely safe.

**Lessons Learned**

- Third‑party risk: breach via TCS credentials shows contractor systems are attack vectors.
- Social engineering + MFA bypass: attackers manipulated staff to reset credentials or allow access.
- Legacy systems: testimony indicated M&S relied on hybrid, outdated IT that hindered quick containment.
- Containment via shutdown: M&S pulled online services quickly, isolating systems.
- Necessity of offline backups: backups must be segmented and immutable.
- Policy & regulation: post-incident, M&S chair called for mandatory cyber-attack reporting to authorities.

**Reference:**

- https://www.mdpi.com/2079-9292/12/21/4494 
- https://www.checkpoint.com/cyber-hub/ransomware/what-is-crypto-ransomware/
- https://www.checkpoint.com/cyber-hub/ransomware/what-is-locker-ransomware/
- https://www.cloudflare.com/en-gb/learning/security/ransomware/petya-notpetya-ransomware/
- https://www.knowbe4.com/ransomware-knowledgebase/locker
- https://sectigostore.com/blog/what-is-scareware-and-scareware-examples/
- https://www.the-web-people.com/blog/inside-the-ms-cyberattack-technical-analysis?utm_source=chatgpt.com  
