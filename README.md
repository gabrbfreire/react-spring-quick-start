# React & Spring Quick-Start

Repository with basic setup to quick start Spring & React projects

Instructions:

-Create a project folder with backend and frontend folders

![ScreenShot](https://user-images.githubusercontent.com/50384743/99128817-a1ad5b80-25ea-11eb-9a84-8ddc5f3bf70f.png)

-Create new Spring project on Spring Initializr and extract it on backend folder

-Create new React project on front end folder

```
create-react-app app-name
```

-Add the following to pom.xml
```xml
<plugin>
   <groupId>com.github.eirslett</groupId>
   <artifactId>frontend-maven-plugin</artifactId>
   <version>1.6</version>
   <configuration>
       <workingDirectory>../frontend/</workingDirectory>
       <installDirectory>target</installDirectory>
   </configuration>
   <executions>
       <execution>
           <id>install node and npm</id>
           <goals>
               <goal>install-node-and-npm</goal>
           </goals>
           <configuration>
               <nodeVersion>v8.11.3</nodeVersion>
               <npmVersion>5.6.0</npmVersion>
           </configuration>
       </execution>
       <execution>
           <id>npm install</id>
           <goals>
               <goal>npm</goal>
           </goals>
           <configuration>
               <arguments>install</arguments>
           </configuration>
       </execution>
       <execution>
           <id>npm run build</id>
           <goals>
               <goal>npm</goal>
           </goals>
           <configuration>
               <arguments>run build</arguments>
           </configuration>
       </execution>
   </executions>
</plugin>
<plugin>
  <artifactId>maven-antrun-plugin</artifactId>
  <executions>
      <execution>
          <phase>generate-resources</phase>
          <configuration>
              <target>
                  <copy todir="${project.build.directory}/classes/static">
                      <fileset dir="${project.basedir}/../frontend/build" />
                  </copy>
              </target>
          </configuration>
          <goals>
              <goal>run</goal>
          </goals>
      </execution>
  </executions>
</plugin>
```
