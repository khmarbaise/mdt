Maven Deployment Tool
=====================

You use Maven to build your artifacts and via mvn release:perform you will
deploy the artifact to a Maven repository.

But then? Isn''t the next locigal step to deploy on a Tomcat, JBoss etc. ? 


Now the step is to extract an artifact (war, ear, etc.) and
deploy it to a single or mutliple servers?


License
-------
[Apache License, Version 2.0, January 2004](http://www.apache.org/licenses/)

Homepage
--------

[http://khmarbaise.github.com/mdt](http://khmarbaise.github.com/mdt)

Status
------

TODOs
-----

Usage
-----

Ideas
-----
- What about the situation:
  Having a Maven project which has been build and now you would like to deploy it.
  -> Have a deployment plugin which handles this ?
     Should be done after release:perform had been done...
     -> Example: mvn release:perform deployment:release
         mvn deployment:release will deploy the release which the most up-to-date (check against the current Maven project ?)

  What about deployment of a SNAPSHOT release ? 
  -> mvn deployment:current
     mvn deployment (the same as above)

- Deploy to a single Tomcat
  -> Think about cargo ? (Can be programmed!) only the configuration might be done 
     somehow
  -> What about multiple instances of Tomcat on a single machine ?

- Deploy to multiple Tomcats on mutliple machines.


- Describe the destination server(s) + configuration into a deployment.xml
  -> Define the artifacts which should be used
  -> Download via aether library 
  -> Define servers etc.

Links
-----

- [Deploy System (svn based)](http://api.mutado.com/mobile/svndeploy/)
  
