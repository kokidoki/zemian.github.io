title=Run Tomcat with webapp-runner.jar
date=2018-06-21
type=post
tags=tomcat, webapp-runner
status=published
~~~~~~

I have used <https://github.com/jsimone/webapp-runner> in several
projects now, and I find it really useful.

You can start a Tomcat instance as simple as this:

    java -jar target/webapp-runner.jar target/adocblog.war

However if you need to run it with extra classpath entries, then you
would need to use the `-cp` instead of `-jar` Java option. Like this:

    java -cp "target/extra-classes:target/webapp-runner.jar" webapp.runner.launch.Main target/adocblog.war
