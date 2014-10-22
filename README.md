vCenter Server Appliance Reverse Proxy
===
If you ever have the need to access your VCSA externally you ought not to expose the actual appliance to the internet.  This is where things like reverse proxies come in real handy. For one thing, you're able to add in an extra layer of authentication. There is, however, one caveat when one wants to have a fully functioning, externally accessible, VCSA and that's the ability to access your guest's console.  Luckily, VMWare and their team of engineers were clever and decided to use a single port, 7331, along with query string variables to dictate which guest you want console access to. 

So what's needed to get started? NGINX, why NGINX? Because it's the right tool for the job! I've included a rather sanitary configuration within this repository to use as a reference for anyone who wants a good starting point. Included is an HTTP => HTTPS redirect. An HTTPS reverse proxy for the VCSA and an HTTPS websocket reverse proxy used for accessing the console of your guests.

## Environment specific configured directives
Below is a list of items you will need to configure specifically to your environment.

 - upstream vcsa-9443 server
 - upstream vcsa-7331 server
 - server_name
 - ssl_certificate
 - ssl_certificate_key