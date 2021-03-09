# FTT-WAR
Java sample WEB APPs in WAR files to deploy at Apache Tomcat

- https://tomcat.apache.org/

Configure the file "tomcat-users.xml" and set your PASSWORD, read all the documentation...

...
```xml
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="PASSWORD" roles="tomcat,manager-gui,admin-gui"/>
  <user username="both" password="PASSWORD" roles="tomcat,role1"/>
  <user username="role1" password="PASSWORD" roles="role1"/>
```
...

**Optional**: real world setup:

- Start a Linux server on the cloud (Azure, Amazon, Google, etc)
- Connect to the Linux server by ssh
- Install Java and Apache Tomcat
- Setup firewall ports as appropriate
- Register a domain name (± R$ 30.00)
- Setup DNS public IP to your domain name
- Setup SSL with Les't Encrypt - https://certbot.eff.org/lets-encrypt/ubuntubionic-other
- Setup Tomcat remote admin (somente depois do SSL configuado) 
  - $CATALINA_HOME/webapps/manager/META-INF/context.xml - [hints](https://stackoverflow.com/questions/36703856/access-tomcat-manager-app-from-different-host)
- Deploy your WAR files (WEB APPs)
- Setup MySQL database on the same server (for learning), in a dedicated server, or as a service and persist your data

> The cloud and the Internet are the labs!
