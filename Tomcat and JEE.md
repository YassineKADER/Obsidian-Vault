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
