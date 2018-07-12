# Load-Balancers-Assignment

Load Balancers & Tomcat assignment for Devops Training 2018

### Setup:

1. Set up 3 tomcat docker containers with the following war https://github.com/efsavage/hello-world-war

2. Set up a HAProxy running on port 80 of your VM.

### Assignment:

1. Setup 2 backends - _web_ (server-1 & server-2) and _backup_ (server-3), with _web_ as the default backend. The other backend must be used when the first 2 backends are down. [5 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.1 and upload it along with a screenshot of the curl request with both server-1 and server-2 down.)_

2. Change index.jsp in war to display "Hello World from backup" and deploy it via tomcat manager on server-3
Using ACLs, implement a routing mechnanism such that any URI ending with **/backup** will be redirected to server-3. [5 points]

   **Bonus**: Make the ACL case insensitive i.e., /backup, /Backup, /BACKUP, /BackUp, etc are valid URI. [5 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.2 and upload it along with a screenshot of the curl request and screenshot of the manager UI)_ 

3. Using ACLs only, blacklist the other VMs' IP on haproxy. Try making a request from that VM now. [10 points]

   _(Rename the haproxy.cfg file to haproxy.cfg.3 and upload it along with a screenshot of the curl request.)_


4. Modify your HAProxy so it can handle SSL/TLS traffic now. All HTTPS traffic must be redirected to server-3. Create a self signed certificate for the same. [20 points]

   **Bonus**: Enforce SSL usage in HAProxy i.e., if the frontend connection was not using SSL, then return a 301 redirect to the same URI, but with "https". [10 points]
   
   _(Rename the haproxy.cfg file to haproxy.cfg.5 and upload it along with a screenshot of the curl requests (Use curl with the -vL flag).)_
 
 5. Change AccessLogValve valve pattern to print the "host" header in accesslog of tomcat in server-3 
   (submit screenshot of access Logs and tomcat config file) [5 points]

**Create a tarball of all the files and mail it to sudhindra.s@media.net**

**\* Deadline is 15/07/2018 (Monday) 12:01 PM**
