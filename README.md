# FTT-WAR
Java sample WEB APPs in WAR files to deploy at Apache Tomcat

- https://tomcat.apache.org/

Configure the file "tomcat-users.xml" and set your PASSWORD, read all the documentation...

...
```xml
  <role rolename="tomcat"/>
    <user username="tomcat" password="PASSWORD" roles="manager-gui,admin-gui"/>
 
```
...

__Optional__: real world setup:

- Start a Linux server on the cloud (Azure, Amazon, Google, etc)
- Connect to the Linux server by ssh
- Install Java 11 (or more) and Apache Tomcat 9 (not 10 for now)
- Setup firewall ports as appropriate (8080)
- Register a domain name (± R$ 30.00 year)
- Setup DNS public IP to your domain name
- Setup SSL with Les't Encrypt - https://certbot.eff.org/lets-encrypt/ubuntubionic-other
- Setup Tomcat remote admin (JUST WITH SSL READY) 
  - $CATALINA_HOME/webapps/manager/META-INF/context.xml - [hints](https://stackoverflow.com/questions/36703856/access-tomcat-manager-app-from-different-host)
- Deploy your WAR files (WEB APPs)
- Setup MySQL database on the same server (for learning), in a dedicated server, or as a service and persist your data

> The cloud and the Internet are the labs!
