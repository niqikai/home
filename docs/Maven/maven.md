# Maven

## How to create a Java project(JAR file)

### Create a Project from Maven Template

```Maven
mvn archetype:generate
  -DgroupId={project-packaging}
  -DartifactId={project-name}
  -DarchetypeArtifactId={maven-template}
  -DinteractiveMode=false
```

```Maven
mvn archetype:generate -DgroupId=com.mkyong.hashing -DartifactId=java-project -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

### Maven Directory Layout

### POM file

> Review the generated pom.xml. It’s quite empty, just a single jUnit dependency.

```XML
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
        http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mkyong.hashing</groupId>
    <artifactId>java-project3</artifactId>
    <packaging>jar</packaging>
    <version>1.0-SNAPSHOT</version>
    <name>java-project</name>
    <url>http://maven.apache.org</url>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>3.8.1</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```

### Update POM

**Add compiler properties to tell Maven use a specified JDK version to compile the source code.**

```XML
    <properties>
    <!-- https://maven.apache.org/general.html#encoding-warning -->
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>
```

## How to create a multi module project

### Directory Structure

### Maven POM

>A Parent POM file, packaging is pom.

```XMl
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- parent pom -->
    <groupId>com.mkyong.multi</groupId>
    <artifactId>java-multi-modules</artifactId>
    <packaging>pom</packaging>
    <version>1.0</version>

    <!-- sub modules -->
    <modules>
        <module>web</module>
        <module>password</module>
        <module>password-sha</module>
        <module>password-md5</module>
    </modules>
</project>
```

> In password module

```XMl
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
        http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <!-- parent pom -->
    <parent>
        <artifactId>java-multi-modules</artifactId>
        <groupId>com.mkyong.multi</groupId>
        <version>1.0</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <!-- password info -->
    <groupId>com.mkyong.password</groupId>
    <artifactId>password</artifactId>
    <version>1.0</version>
    <packaging>jar</packaging>
</project>

```

> In password-md5 module.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
        http://maven.apache.org/xsd/maven-4.0.0.xsd"> 
    <parent>
        <artifactId>java-multi-modules</artifactId>
        <groupId>com.mkyong.multi</groupId>
        <version>1.0</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <!-- password-md5 info -->
    <groupId>com.mkyong.password</groupId>
    <artifactId>password-md5</artifactId>
    <version>1.0</version>
    <packaging>jar</packaging>

    <dependencies>
        <dependency>
            <groupId>com.mkyong.password</groupId>
            <artifactId>password</artifactId>
            <version>1.0</version>
        </dependency>
    </dependencies>

</project>
```
