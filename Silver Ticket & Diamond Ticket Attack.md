# Silver Ticket & Diamond Ticket Attack

## Silver Ticket Attack
In  Silver Ticket we forged a service ticket (TGS) used to access a specific service (like CIFS, HTTP, MSSQL) without needing to contact the KDC.

It allows an attacker to impersonate a user to a service without touching the Domain Controller.

## How Does It Work?
<img width="1920" height="1009" alt="Image from CRTP course" src="https://github.com/user-attachments/assets/dd8db0be-4936-414a-8423-9b490dc628fe" />
Image from CRTP course

The attacker, using the NTLM (RC4) or AES key of a service account (e.g., sqlsvc@domain.local),  forge a TGS for a service (e.g., MSSQLSvc/server.domain.local).

The forged ticket is injected into memory (/ptt) and used to access the service directly.

## What does it mean?
It means that, If we have hash of particular machine, we can access a service on that machine as any user including a domain admin.

## Difference between Golden Ticket and Silver Ticket
In case of Golden ticket, we forge a TGT (Ticket Granting Ticket) where in case of Silver ticket we forge Service ticket

In case of Golden ticket, we can get the access of all the resources as any user on any service on any computer, where in case of Silver ticket, we aimed to get access of particular service on particular machine.

In case of persistence, as the krbtgt account has very less chance of password change, so it has huge age. In case of silver ticket a service account has to be compliant with password policy and usually it changes in 30 days.

## Sample PoC from CRTP Lab
1. Forget a silver ticket for the domain controller machine for HTTP service
<img width="1920" height="472" alt="Image from CRTP course" src="https://github.com/user-attachments/assets/986d8821-a72e-4bd6-9d3c-1458603a4dea" />
Image from CRTP course

3. Confirm the ticket is injected or not using klist command
<img width="1582" height="732" alt="image" src="https://github.com/user-attachments/assets/e802ce21-bf0f-4c58-afe4-73c9f941ea39" />

4. Access the machine using winrs command
<img width="1270" height="482" alt="image" src="https://github.com/user-attachments/assets/17e5bf19-53fd-4861-8871-28a2d97c7a15" />

5. Try accessing other service on domain controller, will result in to exception
<img width="1184" height="220" alt="image" src="https://github.com/user-attachments/assets/212e6c60-edc6-4fb0-a68f-a473349a11b5" />

## Diamond Ticket
In Diamond ticket we request for the TGT and once we received the TGT we modify it and send back to the KDC and the later on steps will remain same.

So we can say that, Golden ticket is ticket forging attack, where the Diamond ticket is ticket re-packaging attack.
<img width="1920" height="1011" alt="image" src="https://github.com/user-attachments/assets/f989b160-7573-44ac-a54d-43f72448b9e8" />

In case of diamond ticket, we would still need a krbtgt secret to decrypt the TGT and after modification to encrypt the TGT. 

A Diamond ticket attack is more opsec friendly then Golden ticket because Golden ticket does,

Not have corresponding TGT request for TGS/Service ticket (Step 1 & step 2).

Not have valid ticket time.

## Sample PoC from CRTP Lab
1. Create a Diamond ticket and inject in current session
<img width="1920" height="366" alt="image" src="https://github.com/user-attachments/assets/978c98ec-821e-47ce-a5a2-f2031f0a89f4" />

2. Access the DC
<img width="1716" height="778" alt="image" src="https://github.com/user-attachments/assets/a51054a2-4735-4eca-899b-c77541593fab" />
 
