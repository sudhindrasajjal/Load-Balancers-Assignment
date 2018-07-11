# Load-Balancers-Assignment

Load Balancers assignment for Devops Training 2018

### Setup:

1. Set up 3 web docker containers with the following content
   * This is web server-1, running on port 8080!
   * This is web server-2, running on port 8081!
   * This is blog server-3, running on port 8082!

2. Set up a HAProxy running on port 80 of your VM.

### Assignment:

1. Setup 2 backends - _web_ (server-1 & server-2) and _blog_ (server-3), with _web_ as the default backend. The other backend must be used when the first 2 backends are down. [5 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.1 and upload it along with a screenshot of the curl request with both server-1 and server-2 down.)_

2. Using ACLs, implement a routing mechnanism such that any URI ending with **/blog** will be redirected to server-3. [5 points]

   **Bonus**: Make the ACL case insensitive i.e., /blog, /Blog, /BLOG, /BlOg, etc are valid URI. [5 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.2 and upload it along with a screenshot of the curl request.)_ 

3. Using ACLs only, blacklist the other VMs' IP on haproxy. Try making a request from that VM now. [10 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.3 and upload it along with a screenshot of the curl request.)_

4. Setup haproxies on both your VMs in active-passive mode. Setup keepalived and VRRP instances on both the boxes. Don't worry much about assigning the VIPs to the instances. Aim of this question is to get familiar with the functioning of Keepalived and how VRRP instance blocks work. [15 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.4 and upload it along with keepalived.conf file.)_

5. Modify your HAProxy so it can handle SSL/TLS traffic now. All HTTPS traffic must be redirected to server-3. Create a self signed certificate for the same. [20 points]

   **Bonus**: Enforce SSL usage in HAProxy i.e., if the frontend connection was not using SSL, then return a 301 redirect to the same URI, but with "https". [10 points]
   
   _(Rename the haproxy.cfg file to haproxy.cfg.5 and upload it along with a screenshot of the curl requests (Use curl with the -vL flag).)_

**Create a tarball of all the files and mail it to sudhindra.s@media.net**

**\* Deadline is 15/07/2018 (Monday) 12:01 PM**
