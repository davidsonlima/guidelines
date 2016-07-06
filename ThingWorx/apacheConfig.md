# Apache Configuration for Windows Server

## Java Startup Configuration

* Add the following lines to improve performance:

``
-XX:+UseNUMA
-XX:+UseConcMarkSweepGC
-XX:PermSize=128m
-XX:MaxPermSize=1024m (or more)
``

* Clear the other memory settings.

## Change HTTP protocol to improve ThingWorx Performance

* Open the `server.xml` file located at [YOUR_INSTALATION_PATH]\Apache Software Foundation\Tomcat 8.0\conf 
* Change the protocol propertie of `< Connector port='HTTP_Chosen_Port' ... > to: ``protocol="org.apache.coyote.http11.Http11NioProtocol"``
