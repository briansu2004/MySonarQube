# MySonarqube

My Sonarqube

## Sonarqube + Jenkins -> Continous Inspection

Use SonarQube Scanner plugin with Jenkins

## Sonarqube + Docker

Easy to use

Saving on configuration

```
docker pull sonarqube
docker images
docker run -d --name sonarqube -p 9000:9000 sonarqube
```

```
http://localhost:9000
```

admin | admin -> sonaradmin

### Output

```
C:\Code\MySonarQube>docker pull sonarqube
Using default tag: latest
latest: Pulling from library/sonarqube
97518928ae5f: Already exists
57709a8c10d4: Pull complete
fa4b951c4c9e: Pull complete
Digest: sha256:ac3a1965cabafb8728a14ac572bb0803b5badb2940bcc289f8fa4b697cd0d6d1
Status: Downloaded newer image for sonarqube:latest
docker.io/library/sonarqube:latest
```

### Analysis the sample project

https://github.com/gouthamchilakala/PetClinic

```
cd \tmp
git clone https://github.com/gouthamchilakala/PetClinic.git
```

```
http://localhost:9000
```

login as admin

Create a new project

Locally

Generate a token

brian: 5475141a0e5dec17c46b369881af2370853f5fc8

for Java Maven project:

configure Maven

http://localhost:9000/documentation/analysis/scan/sonarscanner-for-maven/

Edit the settings.xml file, located in $MAVEN_HOME/conf or ~/.m2, to set the plugin prefix and optionally the SonarQube server URL.

```
<settings>
    <pluginGroups>
        <pluginGroup>org.sonarsource.scanner.maven</pluginGroup>
    </pluginGroups>
    <profiles>
        <profile>
            <id>sonar</id>
            <activation>
                <activeByDefault>true</activeByDefault>
            </activation>
            <properties>
                <!-- Optional URL to server. Default value is http://localhost:9000 -->
                <sonar.host.url>
                  http://localhost:9000
                </sonar.host.url>
            </properties>
        </profile>
     </profiles>
</settings>
```

```
mvn clean verify sonar:sonar \
  -Dsonar.projectKey=test \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=5475141a0e5dec17c46b369881af2370853f5fc8
```

```
C:\Apps\apache-maven-3.8.4\bin\mvn clean verify sonar:sonar -Dsonar.projectKey=test -Dsonar.host.url=http://localhost:9000 -Dsonar.login=5475141a0e5dec17c46b369881af2370853f5fc8
```

Try

```
sonar-scanner.bat -D"sonar.projectKey=test" -D"sonar.sources=." -D"sonar.host.url=http://localhost:9000" -D"sonar.login=c0b19af2cda542eda5d0cb8d731f7680bea8ffda"
```

Create a configuration file in your project's root directory called sonar-project.properties

```
# must be unique in a given SonarQube instance
sonar.projectKey=my:project

# --- optional properties ---

# defaults to project key
#sonar.projectName=My project
# defaults to 'not provided'
#sonar.projectVersion=1.0

# Path is relative to the sonar-project.properties file. Defaults to .
#sonar.sources=.

# Encoding of the source code. Default is default system encoding
#sonar.sourceEncoding=UTF-8
```

```
docker run \
    --rm \
    -e SONAR_HOST_URL="http://${SONARQUBE_URL}" \
    -e SONAR_LOGIN="myAuthenticationToken" \
    -v "${YOUR_REPO}:/usr/src" \
    sonarsource/sonar-scanner-cli
```

```
docker run --rm -e SONAR_HOST_URL="http://localhost:9000" -e SONAR_LOGIN="c0b19af2cda542eda5d0cb8d731f7680bea8ffda" -v "C:\tmp\PetClinic:/usr/src" sonarsource/sonar-scanner-cli
```

Download and unzip Sonar Scanner for Windows

```
cd C:\tmp\map-flatmap-simple-01
call C:\Apps\sonar-scanner-4.7.0.2747-windows\bin\sonar-scanner.bat -D"sonar.projectKey=test" -D"sonar.sources=." -D"sonar.host.url=http://localhost:9000" -D"sonar.login=c0b19af2cda542eda5d0cb8d731f7680bea8ffda"
```

### Output

```

```

### Troubleshooting

May need to set up JDK_HOME and MAVEN_HOME.

```
set JAVA_HOME=C:\Apps\Java\jdk-17
set MAVEN_HOME=C:\Apps\apache-maven-3.8.4
```

## SonarLint

Integrated with IDE

## Sonarqube

Code Quality and Code Security

SonarQube includes support for the programming languages Java (including Android), C#, C, C++, JavaScript, TypeScript, Python, Go, Swift, COBOL, Apex, PHP, Kotlin, Ruby, Scala, HTML, CSS, ABAP, Flex, Objective-C, PL/I, PL/SQL, RPG, T-SQL, VB.NET, VB6, and XML.[9] As of December 2021, analyzing C, C++, Obj-C, Swift, ABAP, T-SQL and PL/SQL is only available via a commercial license.

SonarQube integrates with Eclipse, Visual Studio, Visual Studio Code, and IntelliJ IDEA development environments through the SonarLint plug-ins, and also integrates with external tools like LDAP, Active Directory, GitHub, and others. SonarQube is expandable with the use of plug-ins.

## Sonarqube components:

- Sonarqube server
- Sonarqube dashboard
- Sonarqube scanner
- Sonarqube database server

## Misc

### VSCode change terminal font size

Settings (Ctrl+,)

```
terminal.integrated.fontSize=13
```
