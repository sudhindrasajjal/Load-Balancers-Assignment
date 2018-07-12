# Load-Balancers-Assignment
## sample war source https://github.com/efsavage/hello-world-war

Load Balancers & Tomcat assignment for Devops Training 2018

### Setup:

1. Set up 3 tomcat docker containers
   - Change Connector port to 8080 , 8081 , 8082 respectively
   - Set heap Dump Max value to 512 M , min value to 128 M

2. Set up a HAProxy running on port 80 of your VM.

### Assignment:

1. Setup 2 backends - _web_ (server-1 & server-2) and _backup_ (server-3), with _web_ as the default backend. The other backend must be used when the first 2 backends are down. **[5 points]**

   _(Rename the haproxy.cfg file to haproxy.cfg.1 and upload it along with a screenshot of the curl request with both server-1 and server-2 down.)_

2. 
    a) enable Tomcat manager with role as manager and password as your adName **[5 points]**
        - login to manager

    b) Build the war **[5 points]**
        - `mvn install` will build the war and place it in the target folder.

    c) Deploy the war to Tomcats **[10 points]**
        - By Copying to webapps
        - And Via manager

    d) Change index.jsp in war to display "Hello World from backup" build again using `mvn clean install` and deploy it via tomcat manager on server-3 **[5 points]**

    **Bonus:**

    e) Vhosts: **[10 points]**
        
	* Add /etc/hosts entry for www.tomcat-app1.com and www.tomcat-app2.com to point to the IP where tomcat is installed
	* build 2 wars by modifying the src/main/webapp/index.jsp file and build again using `mvn clean install`
	* the name of the war can be app1.war and app2.war
	* create folders app1_webapps and app2_webapps add copy the app1.war and app2.war to their respective folders
	* Add 2 hosts entries with app1_webapps and app2_webapps as the new appbases
	* The vhosts if working fine should pickup app1.war and app2.war from app1_webapps and app2_webapps for www.tomcat-app1.com and www.tomcat-app2.com.

    f) verify the following OOM Exception on catalina.out when 0.0.0.0:8080/hello-world-war-1.0.0/oom is hit. **[5 points]**
    
    `Exception in thread "http-nio-8080-exec-74" java.lang.OutOfMemoryError: Requested array size exceeds VM limit`


3. Using ACLs, implement a routing mechnanism such that any URI ending with **/backup** will be redirected to server-3. **[5 points]**

   **Bonus**: Make the ACL case insensitive i.e., /backup, /Backup, /BACKUP, /BackUp, etc are valid URI. **[5 points]**

   _(Rename the haproxy.cfg file to haproxy.cfg.3 and upload it along with a screenshot of the curl request and screenshot of the manager UI)_ 

4. Using ACLs only, blacklist the other VMs' IP on haproxy. Try making a request from that VM now. **[10 points]**

   _(Rename the haproxy.cfg file to haproxy.cfg.4 and upload it along with a screenshot of the curl request.)_


5. Modify your HAProxy so it can handle SSL/TLS traffic now. All HTTPS traffic must be redirected to server-3. Create a self signed certificate for the same. **[20 points]**

   **Bonus**: Enforce SSL usage in HAProxy i.e., if the frontend connection was not using SSL, then return a 301 redirect to the same URI, but with "https". **[10 points]**
   
   _(Rename the haproxy.cfg file to haproxy.cfg.5 and upload it along with a screenshot of the curl requests (Use curl with the -vL flag).)_
 
6. Change AccessLogValve valve pattern to print the "host" header in accesslog of tomcat in server-3
   (submit screenshot of access Logs and tomcat config file) **[5 points]**

**Create a tarball of all the files and mail it to sudhindra.s@media.net**


**\* Deadline is 15/07/2018 (Monday) 12:01 PM**
