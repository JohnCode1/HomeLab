1. go to cloudflair or provider of choice and obtain a domain name WARNING make sure the tld ex .us or .net allows Masking of your information to prevent spam to your info used to buy this domain
2. go to dns and add type A record with name @ and enter your domain name and add a cname certificate with name * and ip running your apps if running streaming apps like jellyfin disable proxy *WARNING if you do not disable proxy for streaming apps you will viloate cloudflares terms of service
3. go to your profile and create api token and click use template for edit zone dns include all zones -> continue to summary and copy api token
4. pull the docker file and edit api key and domain names
5. run docker file and check logs
6. if you want to open it to the wan set the ip in cloudflair or provider of choice to your public ips and open your https https port on your router but do so at your own risk this is not recommended at the stage of this guide and it is recommended to use a overlay vpn like netbird
7. log in with admin@example.com  and password changeme and change your login credentials
8. click on ssl certificate and add your domain and a wildcard
9. check use a dns challenge and select your provider and add a api token and save.
10. test it out by go to host add a proxy host and for domain add your root domain and add port 8888 for the hellome container check block common exploits go to ssl select your certifical select all checks here force ssl, http/2 support, hsts subdomains, and hsts enabled
11. Will keep adding to this as I set this up for my apps: for jellyfin go to networking and change your known proxy to the ip of your ngix proxy manager, if opening jellyfin to worl wide web please read there documentation for ngix set up as you have to do custom settings
12. enable web socket support for jellyfin
13. if you want to use subdomains:
  14. use the custom locations tab in ngix
Next: [WindowsVM](../WindowsVM)
Layout: [Layout](../Layout)
