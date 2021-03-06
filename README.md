# FTT-WAR
Java sample WEB APPs in WAR files to deploy at Apache Tomcat

- https://tomcat.apache.org/

Configure the file "tomcat-users.xml" and set your PASSWORD, read all the documentation...

...
```xml
<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user username="tomcat" password="x6wqpw3QFm2Njv1J" roles="manager-gui,admin-gui"/>
<!-- Do not set user name tomcat, admin, root set some not so obvious name
    and a crazy long strong password  -->
 
```
...

__Optional__ - real world setup:

- Start a Linux server on the cloud (Azure, Amazon, Google, etc)
- Connect to the Linux server by ssh (secure command line - [Filezilla](https://filezilla-project.org/) works too)
- Install Java 11 (or more) and Apache Tomcat 9 (not 10 for now)
- Setup firewall ports as appropriate (8080)
- Register a domain name (± R$ 30.00 year)
- Setup DNS public IP to your domain name (setup subdomain)
- Setup SSL with Les't Encrypt - https://certbot.eff.org/lets-encrypt/ubuntubionic-other
- Setup the .pen SSL file at Apache Tomcat server.xml file...
- Setup Tomcat remote admin (JUST WITH SSL READY) 
  - $CATALINA_HOME/webapps/manager/META-INF/context.xml - [hints](https://stackoverflow.com/questions/36703856/access-tomcat-manager-app-from-different-host)
- Deploy your WAR files (WEB APPs)
- Setup MySQL database on the same server (for learning), in a dedicated server, or as a service and persist your data

Configurar SSL Let's Encrypt no arquivo ../conf/server.xml (copiar arquivos .pem e ajustar permissões)

```xml
<Connector port="8080" protocol="org.apache.coyote.http11.Http11NioProtocol"
maxThreads="150" SSLEnabled="true">
  <SSLHostConfig>
	  <Certificate certificateFile="conf/ssl/cert.pem"
		  certificateKeyFile="conf/ssl/privkey.pem"
		  certificateChainFile="conf/ssl/chain.pem" />
  </SSLHostConfig>
</Connector>
```

> The cloud and the Internet are the labs!
