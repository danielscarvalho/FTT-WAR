# FTT-WAR
Java sample WEB APPs in WAR files to deploy at Apache Tomcat

- https://tomcat.apache.org/

- Configuração no .profile do Linux:

```
export JAVA_HOME=/opt/jdk-17
export CATALINA_HOME=/opt/apache-tomcat-10
export PATH=$PATH:$JAVA_HOME/bin:/opt/apache-maven-3.6.3/bin
export CLASSPATH=$JAVA_HOME/lib:$CATALINA_HOME/lib
```

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

Configure managment apps to be accessed not only from 127.0.0.1 (localhost):

/webapps/manager/META-INF/context.xml<br>
/webapps/host-manager/META-INF/context.xml

```xml
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="\d+.\d+\.\d+\.\d+" />

```

__Optional__ - real world setup:

- Start a Linux server on the cloud (Azure, Amazon, Google, Vultr, etc)
- Connect to the Linux server by ssh (secure command line - [Filezilla](https://filezilla-project.org/) works too)
- Install Java 17 (or more) and Apache Tomcat 10
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
  <UpgradeProtocol className="org.apache.coyote.http2.Http2Protocol" />
  <SSLHostConfig>
	  <Certificate certificateFile="conf/ssl/cert.pem"
		  certificateKeyFile="conf/ssl/privkey.pem"
		  certificateChainFile="conf/ssl/chain.pem" />
  </SSLHostConfig>
</Connector>
```
There is another way, more simple, to create a key for SSL without a third party, such as Let's Encrypt. You can do it with Java and self sign the key (at Linux):

```
$JAVA_HOME/bin/keytool -genkey -alias tomcat -keyalg RSA
```

at server.xml:

```xml
<!-- Define an SSL Coyote HTTP/1.1 Connector on port 8443 -->
<Connector
    protocol="org.apache.coyote.http11.Http11NioProtocol"
    port="8080"
    maxThreads="150"
    SSLEnabled="true">
  <SSLHostConfig>
    <Certificate
      certificateKeystoreFile="${user.home}/.keystore"
      certificateKeystorePassword="the same crazy pwd you created with the key"
      type="RSA"
      />
    </SSLHostConfig>
</Connector>
```


This way you are going to have the encryption, but an alert at the browser that it is not issued by a certification authority.

More details at Tomcat docs: https://tomcat.apache.org/tomcat-10.0-doc/ssl-howto.html


Hosting options: https://linuxhandbook.com/free-linux-cloud-servers/

> The cloud and the Internet are the labs!
