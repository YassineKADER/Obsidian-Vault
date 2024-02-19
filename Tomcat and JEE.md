First Build the app with this command for (maven):
```shell
mvn clean package
```
you'll get a war package this can be used by the servlet container run this case Tomcat, so I'll use docker instead of install tomcat locally:
```shell
docker run -d --name my-tomcat -p 8080:8080 tomcat #to run the tomcat image the container name is my-tomcat
docker cp locationtowarfile.war comtainername:/usr/local/tomcat/webapps/
```
for the war file most of time you'll find it on YourServletProject/target
you can check the deployment status by seeing the logs of the container:
```shell
docker logs container-name
```
you servlet will be available at `localhost:8080/warfilename`
Also you may have a maven version problem you can fix it by that:
```xml
<properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
    </properties>
```
### Simple script to build and deploy the servlet

```bash
#!/bin/bash



# Build the project with Maven

mvn clean package

  

# Check if the build was successful

if [ $? -eq 0 ]; then

    echo "Build successful. Copying the .war file to Docker container..."

  

    # Copy the .war file to the Docker container

    docker cp servlets/servlet/target/servlet-1.0-SNAPSHOT.war my-tomcat:/usr/local/tomcat/webapps/test.war

  

    echo "Copy successful."

else

    echo "Build failed. Please check the error messages and try again."

fi
```
