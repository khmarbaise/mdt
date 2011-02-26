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
- May be we should about two ways:
  Maven Deployment Tool Plugin (which can be configured into a project)
    -> mvn mdt:release -> get latest release version
    -> mvn mdt:current

  Maven Deployment Tool (mdt) via command line.
  mdt deployment

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

- Deployment of a cli application ? 

- Introduce a life-cycle for deployment

  validate            => pre check if configuration is ok ? May be other things?
  initialize

  prepare-download
  download            => Download Tomcat ? Really need if we think about a concept like Maven
  post-download

  prepare-install
  install             => Install Tomcat on a machine
  post-install
  
  prepare-deployment  => Idea: Call mvn release:prepare release:perform
  deployment          => deploy generated artifacts with the mvn release before to the tomcat
  post-deployment     => Cleanups ?

  prepare-deployment-tests 
  deployment-tests         => check to see if deployment was successful or not?
  post-deployment-tests

  verify


  mdt clean ? (we put anything which generated etc. into mdt folder

               Maven Project (war)
                 +-- pom.xml
                 +-- deployment.xml
                 +-- src
                 +-- target
                 +-- mdt
        
    super-deployment.xml which contains already defined steps like in Maven the Super-POM (Plugins?)
 

  mdt verify local (local machine?)
  mdt verify dev (different machine?)
  mdt verify test
  mdt verify pre-production
  mdt verify production

   ?  pre-dev, post-dev, dev, pre-test, test, post-test, pre-production, production

  The dev, test, pre-production and production will be defined in the deployment.xml
    (may be a list of already defined in the Super-deployment.xml


- Describe the destination server(s) + configuration into a deployment.xml
  -> Define the artifacts which should be used
  -> Download via aether library 
  -> Define servers etc.

   <deployments>
     <servers>
       <server>
        <group>production</group>>
        <id>s1</id>
       </server>
       <server>
        <group>production</group>>
        <id>s2</id>
        ...
       </server>
     </servers>
     <deployment>
       <id>production</id>
       <group>production</group>
     </deployment>
     <deployment>
       <id>test</id>
     </deployment>
   </deployments>

Links
-----

- [Deploy System (svn based)](http://api.mutado.com/mobile/svndeploy/)
  
