### Install Apache Tomcat
1. Download Zip
2. Setup JAVA_HOME, CATALINA_HOME
3. bin\startup.bat

### Generate OpenGrok configuration.xml
1. Use Command
C:\Apps\Java\jdk1.7.0_76\bin\java.exe -jar C:\Apps\opengrok-0.12.1.5\lib\opengrok.jar -W C:\Apps\OpenGrok\configuration.xml -c C:\Apps\ctags58\ctags.exe -P -S -v -s C:\Apps\OpenGrok\src -d C:\Apps\OpenGrok\grokdata

### Modify opengrok source.war WEB-INF\web.xml
1. Properly put configuration.xml path
2. Zip and rename to .war again
3. put under Tomcat\webapps
4. Launch server

### References

1. http://www.ntu.edu.sg/home/ehchua/programming/howto/Tomcat_HowTo.html
2. http://algopadawan.blogspot.com/2012/07/installing-opengrok-on-windows.html
3. http://www.tnvbalaji.net/2015/06/09/how-to-install-opengrok-on-windows-os/
4. https://jdevel.wordpress.com/2011/03/26/running-opengrok-on-windows/
5. https://github.com/OpenGrok/OpenGrok/wiki/How-to-install-OpenGrok#uStep1u__Deploy_the_web_application
