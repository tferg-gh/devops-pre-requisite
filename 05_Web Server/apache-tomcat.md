Apache Tomcat provides a web server environment for web appllcations written in Java. 

#### Install
Apache Tomcat is installed by compiling the source code downloaded from a .tar.gz. For production environments you would setup Tomcat as a service but for the purpose of learning, this method is fine too.

##### Simple
Determine the vesion of Tomcat & Java you need installed 

https://tomcat.apache.org/whichversion.html

Download and install the Java JDK

[[just-enough-java#Installing Java]]

Download the tar.gz from the Apache Tomcat website

https://dlcdn.apache.org/tomcat/tomcat-10/v10.0.21/bin/apache-tomcat-10.0.21.tar.gz

[[curl]]

Extract the archive

[[tar]]

Run the startup script
```
./apache-tomcat-X.X.X/bin/startup.sh
```

#### Verify
Tomcat uses port 8080 by default so go to your loopback address at port 8080 to verify it is installed.

[[ip]]

You can also just curl the webpage at http://localhost:8080 and it should return the html

#### Directory
Inside the installation directory for Tomcat will look like this:

```
..
bin - Contains all the .sh scripts and .bat files for Windows
conf - Contains all the configuration files for the webserver
lib
logs - Contains all the logs
temp
webapps - This is the directory you would store your application
work
```

The bin dir contains the startup.sh and shutdown.sh scripts which are used to stop and start the server

The conf dir contains the server.xml file which is where you can specify the port the conector listens on and the web.xml is where you can configure web applications. 

The logs dir contains logs which is a good place to look if you're running into issues. Check the catalina.out log for information on web application deployments from a .war archive

#### Deploying a web application
When you build an application using Java or one of the Java build tools like Maven or Gradle, you would take the app.war file and put it in the /webapps dir. If Tomcat is running it will extract the .war file and store it in a directory of the same name. This application is hosted at that path and requires a restart of Tomcat?


