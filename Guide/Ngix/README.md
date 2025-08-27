1. go to cloudflair or provider of choice and obtain a domain name WARNING make sure the tld ex .us or .net allows Masking of your information to prevent spam to your info used to buy this domain
2. go to dns and add type A record with name @ and enter local ip address running ngix proxy add another type A * and ip running your apps if running streaming apps like jellyfin disable proxy
3. go to your profile and create api token and click use template for edit zone dns include all zones -> continue to summary and copy api token
4. pull the docker file and edit api key and domain names
5. run docker file and check logs
6. if you want to open it to the wan set the ip in cloudflair or provider of choice to your public ips and open your https https port on your router but do so at your own risk this is not recommended at the stage of this guide and it is recommended to use a overlay vpn like netbird
Next: [WindowsVM](../WindowsVM)
Layout: [Layout](../Layout)
