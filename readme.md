## How to create this Github maven repository.

1. Use maven deploy your maven project to local file system (maven-repo).  
```
mvn deploy -DaltDeploymentRepository=minis-maven-repo::default::file:/minis/maven-repo/repository  
```

2. Create maven-repo project on Github.  

3. Commit and push local repository to Github.
```
cd /minis/maven-repo  
git init  
git add repository/*  
git commit -m "deploy maven-repo"  
git remote add origin https://github.com/minis/maven-repo.git  
git push -u origin master  
```

4. Check https://github.com/minis/maven-repo  


## If use maven-release-plugin.  
Can use it to release and deploy.  
```
mvn release:prepare  
mvn release:perform -Darguments=-DaltDeploymentRepository=minis-maven-repo::default::file:/minis/maven-repo/repository  
```


## How to use this maven repository.

Config pom.xml for your project.   

1. Add custom repository.  
```xml
<repositories>
    <repository>
        <id>minis-maven-repo</id>
        <name>the minis maven repository</name>
        <url>https://raw.githubusercontent.com/minis/maven-repo/master/repository</url>
    </repository>
</repositories>
```

2. Add minis library dependency. Ex: minis-speech  
```xml
<dependencies>
    <dependency>
        <groupId>net.minis</groupId>
        <artifactId>minis-speech-api</artifactId>
        <version>0.0.1-SNAPSHOT</version>
    </dependency>
</dependencies>
```
