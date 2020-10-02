# FTT-WAR
Java sample WEB APPs in WAR files to deploy at Apache Tomcat

- https://tomcat.apache.org/

Configure the file "tomcat-users.xml" and set your PASSWORD, read all the documentation...

...
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="PASSWORD" roles="tomcat,manager-gui,admin-gui"/>
  <user username="both" password="PASSWORD" roles="tomcat,role1"/>
  <user username="role1" password="PASSWORD" roles="role1"/>
...
