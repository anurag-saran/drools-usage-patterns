# Drools Usage Patterns
There are 3 ways to use the Drools platform, this project showcases the differences:

1. Embedded/Generate
  * Inspect the `drools-usage-patterns-embedded` project to see how to use rules that are on your classpath
   EmbeddedKieBaseProvider.java : Any Rules in the classPath are added. i.e. src/main/resources/name.drl
	```shell
   		KIE_CONTAINER = KieServices.Factory.get().newKieClasspathContainer();
	```
  * dependency: drools-usage-patterns-model
  
2. Scanner 
  * Inspect the `drools-usage-patterns-fetch` project to see how to use rules that are fetched with maven, potentially changing without updating your code!
  * KieBaseProvider.java
	```shell
  	//The releaseId uses maven groupId, artifactId, and version to specify a kjar (set of rules)
	String groupId = "com.rhc.drools.example";
	String artifactId = "drools-usage-patterns-kjar";
	String version = "1.0.0-SNAPSHOT";
	ReleaseId releaseId = KIE_SERVICES.newReleaseId(groupId, artifactId, version);
	```
 * dependency: drools-usage-patterns-model
 
3. Remote 
  * Inspect the `drools-usage-patterns-remote` project to see how to create a client for the realtime execution server, introduced in the latest version of Drools.
  * RemoteCommandExecutor.java
  ```shell
	     //Creating a client to the KieServer requires a url, and username/password for a user
	    //with the 'kie-server' role.
	    String url = "http://localhost:8080/kie-server/services/rest/server";
	    String username = "kieserver";
	    String password = "Pass@123";
 ```
4. drools-usage-patterns-kjar
  * kjar with a single rule.
  * dependency: drools-usage-patterns-model
  
5. drools-usage-patterns-model
  * jar with the person object on which the rule is applied.
