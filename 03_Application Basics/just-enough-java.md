Java is a free and opensource coding langugage used to build applications for desktop, mobile and web. 

Applications will often use different versions of Java to run and you will likely see some orrganizations stuck at version 8 because in version 9 they introduced changes that made a number of popular tools and libraries incompatible as well as new licensing. 

Before version 9, Oracle released the JDK (Java Developement Kit) and the JRE (Java Runtime Environment) seperatly. After it is all combined into the JDK. 

If you're looking to download an older verision of the JDK (Pre 17 and 18) you need to go to the OpenJDK website, not the Oracle website. 

Prior to version 9 the versioning is done as 1.8. With version 9 and later the naming convention is just 9.

The JDK helps you create, build and run Java applications. So you're not installing Java but rather a suite a tools to help do that.

You can use any text editor to write java applications but to debug your application you would use the Java Debug Tool (jdb) and to document your application you would use the Java Documentation tool (javadoc). To build and complile your tool you would use the Java Complier (javac). The Jar tool helps to archive all the related tools and libraries into a single Jar file. To run the application you need the Java Runtime Environment (JRE). The Java command line utility is simply called java and is referred to as the loader. This tool is used to run the application.

These tools are available in the jdk-X.X.X/bin directory along with many others.

To check the version of java installed on a system you need to run:

```
java -version
```

#### Installing Java

Downloading and installing the JDK on a Linux system via the command line can be tricky, as there are a number of steps required using different tools. If you're unfamiliar with the tools it can be challenging. 

First you need to identify the version you're using and find the link to download the [[tar]](referred to as a tarball). 

If you're getting the latest version (17 ro 18) you can find the link on the Oracle main website. https://www.oracle.com/java/technologies/downloads/

Oracle.com > Products > Hardware: Java > Java SE > Products > Java JDK

To find the link for older versions of Java go to the http://jdk.java.net/archive/

Your link should look something like this: 

https://download.java.net/java/GA/jdk13.0.2/d4173c853231432d94f001e99d882ca7/8/GPL/openjdk-13.0.2_linux-x64_bin.tar.gz

Note the .tar.gz at the end of the link

It can be tricky to navigate the jdk.java.net website since they want you to use the bulky Oracle one. 

Okay, now that you've got the link you're going to have to download it to the host. You can use wget or [[curl]] to do this. I've only done curl for now.

Note: if you're downloading the file to directory on linux outside of your home directory you'll need sudo privileges.

```
sudo curl https://download.java.net/java/GA/jdk13.0.2/d4173c853231432d94f001e99d882ca7/8/GPL/openjdk-13.0.2_linux-x64_bin.tar.gz --output /opt/openjdk-13.0.2_linux-x64_bin.tar.gz
```

I typically copy the link twice, once after the curl command and once after the directory and then I'll just delete the URL and am just left with the actual file name. 

The output should look like this: 

![[Pasted image 20220601112713.png]]

Okay so no you've got that downloaded you will need to extract it. The file is in a tarball denoted by the .tar.gz so you will use the tar command to extract it. 

You'll need sudo privelages again for this since we're working outside your home directory

The command you'll use is like this:

```
sudo tar -xzvf /opt/openjdk-13.0.2_linux-x64_bin.tar.gz -C /opt/
```

The switches at the start are like options, they stand for:

c = compress
x = extract
z = gzip
v = verbose (display progress on the screen)
f = filename (lets you pick the filename where it is extracted) 

The -C lets you extract the files to a specific directory, otherwise it will just extract into the current directory. 

After you've extracted the files you can run the java command with -version to verify it's working

```
/opt/jdk-13/bin/java -version
```

Now you don't want to have to use the full path to the binaries every time so we can add an environment variable to the system to include that path. 

```
export PATH=$PATH:/opt/jdk-13/bin
```

So now when you type java or any of the other tool names, the system will use the binaries in this directory.

Java source code typically has the extension .java e.g. MyClass.java and when you complie it, it will change to .class.

Say this is your source code

```
MyClass.java
public class MyClass {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

You would then compile the code using javac

```
javac MyClass.java
```

This will output a file MyClass.class

Then you would run it by doing:

```
java MyClass
```

Note how you didn't Refernce the file but rather the class. Need to confirm whether you're just omitting the .class or whether you need to refer to the class inside the file to run it.

Java applications are converted into bytecode before being run on a Java Virtual Machine. This allows Java to be written and run on any system. 

If you're compiling an application with many classes and dependencies, you would use the JAR (Java Archiver) to package them together. 

If the application has embedded images and html files then you would package that using the WAR (Web Archive) file. 

```
jar cf MyApp.jar MyClass.class Service1.class Service2.class 
```

This will package the files and output a file as specificed MyApp.jar which contains all the classes specified. It will also generate a manifest file at META-INF/MANIFEST.MF which contains all the metadata about the archive.

To run an application packaged as a .jar file you need to specify the -jar option as below:

```
java -jar MyApp.jar
```

Usign the javadoc command you can package your .java source code file as a HTML file that is easily read 

```
javadoc -d doc MyClass.java
```

The text after -d will be the name of the folder

Build Tools

When you're working with larger teams or bigger codebases the above process can become unmanageable. This is where some additional tools come in to help manage the build process. 

Maven, Gradle, ANT are some popular ones. They essentially work to automate the build process by utilizing a build file that specifies each step of the process so instead of having to do each step manually, you can rely on the build file to just run a single command. 

Something else to note about running java applications from the command line, it appears you can't just specify the directory that the class file is in and run it, you need to actually be in the directory to run it.

```
java /opt/app/MyClass
```

The above wouldn't work, you would need to cd to /opt/app first then run java MyClass

```
cd /opt/app/
java MyClass
```

Okay it seems like maybe you can run class files from another directory with the -cp switch after java.

I would certainly like to know more about Maven, ANT and Gradle. 

