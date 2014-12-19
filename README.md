dependency-example
==================

Shows issue with overlaying artifacts from 2 different webapps

After you do a 'mvn clean install' you will see that the resultant project-webapp/target/project-1.0-SNAPSHOT/WEB-INF/lib directory has only Spring 4.0.0 artifacts.

spring-aop-4.0.0.RELEASE.jar
spring-beans-4.0.0.RELEASE.jar
spring-context-4.0.0.RELEASE.jar
spring-core-4.0.0.RELEASE.jar
spring-expression-4.0.0.RELEASE.jar
spring-web-4.0.0.RELEASE.jar
spring-webmvc-4.0.0.RELEASE.jar

Now bump the bootstrap-webapp version in it's pom.xml to 1.1-SNAPSHOT and then bump the spring version in the root pom.xml file to 4.0.5.RELEASE. This will cause the project-webapp to continue to use bootstrap-webapp-1.0-SNAPSHOT (which still depends on spring 4.0.0) but the project-webapp will want to bring in spring 4.0.5 artifacts.

Do another 'mvn clean install' (from the root of the project) and now notice there are both versions of the spring artifacts in project-webapp/target/project-1.0-SNAPSHOT/WEB-INF/lib

spring-aop-4.0.0.RELEASE.jar
spring-aop-4.0.5.RELEASE.jar
spring-beans-4.0.0.RELEASE.jar
spring-beans-4.0.5.RELEASE.jar
spring-context-4.0.0.RELEASE.jar
spring-context-4.0.5.RELEASE.jar
spring-core-4.0.0.RELEASE.jar
spring-core-4.0.5.RELEASE.jar
spring-expression-4.0.0.RELEASE.jar
spring-expression-4.0.5.RELEASE.jar
spring-web-4.0.0.RELEASE.jar
spring-web-4.0.5.RELEASE.jar
spring-webmvc-4.0.0.RELEASE.jar
spring-webmvc-4.0.5.RELEASE.jar
