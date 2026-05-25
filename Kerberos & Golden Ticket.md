# Kerberos & Golden Ticket
Kerberos is a ticket-based authentication system that allows users and services to authenticate without sending their password across the network. Instead, a ticket (a piece of data that proves the identity of the user or service) is issued by a trusted third party, called the Key Distribution Center (KDC). 

Kerberos is commonly used in environments where centralised authentication is needed, especially in Windows Active Directory (AD) networks, such as Network File Shares, Domain Controller Authentication.

## How Kerberos works
<img width="1920" height="1274" alt="image" src="https://github.com/user-attachments/assets/cd32c7a9-3fb6-4ec0-bf4c-f65850167372" />

Image from CRTP course
 

Step 1: A client (on behalf of user) sends timestamp that is encrypted using NTLM or AES of the user and sends it to KDC/DC.

Step 2: Domain controller decrypt the timestamp, generate and sends a TGT (Ticket that grants ticket) which is signed/encrypted using the secret of the special user account called "krbtgt". Client can not decrypt the ticket as it does not have access to krbtgt secret.

Step 3: Client sends the TGT back to the DC as a proof of possession of TGT, that means the client is authenticated and request for TGS or service ticket to access specific service.

Step 4: DC perform only validation at this step is, DC will just decrypt the TGT, if its not then responds with auth failed and if all good that means everything is good and generates a TGS to the client. TGS is encrypted with the secret of the target service we want communicate.

Step 5: The client then sends the TGS to service.

Step 6: The service then authorise the client using the TGS.

## Why Kerberos is Consider Secure
- Strong Encryption: Kerberos uses strong encryption algorithms (such as AES) to protect the tickets and credentials. This means the actual password is never sent over the network.
- Replay Protection: Kerberos tickets have timestamps and expiration times to prevent replay attacks (using old tickets to impersonate the user).

**Note:** Before performing a Golden Ticket attack, we assume that we already got the Domain Admin. An attacker perform the Golden Ticket attack for persistence and not something like PE.

## Golden Ticket Attack
In Golden ticket attacker, we exploit the step 3 because the only validation at the end of step 3 is if the DC can decrypt the TGT. 

We grab the AES key of krbtgt account and forge new TGT keys using that AES key and write that this TGT is for domain administrator.

Send the forged ticket to DC (Step 3) without performing the step 1 & step 2 of kerberos authentication, DC will do validation and as its correct, it responds with the service ticket for domain administrator.

Only forge a golden ticket with active domain admin user not with dormant or inactive domain admin (check logoncount while enumeration)

## Sample PoC from CRTP Lab
1. Start the new process as domain admins
<img width="1920" height="299" alt="image" src="https://github.com/user-attachments/assets/203950e9-d27d-4e28-ac97-8ca455a3fcc5" />

2. From the new process, perform the DCSync attack to acquire the krbtgt hash.
<img width="1920" height="308" alt="image" src="https://github.com/user-attachments/assets/f86b4ab6-d61a-4f62-9afe-a382dffdbd38" />

3. Once acquired, forge a new ticket using krbtgt hash and send it to the KDC (Step 3), below commands just generate the ticket forging command by getting the user details such as, id,pgid, domain,pwdlastsetetc…
<img width="1920" height="274" alt="image" src="https://github.com/user-attachments/assets/1109a4b8-361e-4a1e-aae9-c9693ef5ee25" />
<img width="1920" height="163" alt="image" src="https://github.com/user-attachments/assets/50b309f5-05cc-48e2-b896-c38f02694ce8" />

4. Injecting a ticket in current session.
<img width="1920" height="245" alt="image" src="https://github.com/user-attachments/assets/bc2d35e5-b3c8-4704-9a65-07ce670b23ed" />
<img width="1198" height="606" alt="image" src="https://github.com/user-attachments/assets/5bc5708e-ea8e-483e-97ee-7197535132bc" />

## Remediation
- Monitor Kerberos Event ID 4769 (TGS Requests) for anomalies.
- Enforce strict credential rotation.
- Use Windows Defender Credential Guard to prevent ticket injection.
