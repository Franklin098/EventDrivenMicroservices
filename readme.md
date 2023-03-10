# Event Driven Microservices Project

## Project Configuration

### Create new Maven Project

```
brew install maven

mvn --version

mvn archetype:generate -DgroupId=com.franklin -DartifactId=franklinservices -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

Instructions: https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html

### Adjusting Dependencies

**Dependency Management**: configure the parent project, so that all our sub-projects can pick all the dependencies they want.

```
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-dependencies</artifactId>
        <version>${spring.boot.dependencies.version}</version>
        <scope>import</scope>
        <type>pom</type>
      </dependency>
    </dependencies>
  </dependencyManagement>

```

**Dependencies**: all our sub-modules will contain these dependencies without explicitly declare them in their pom.xml

```
  <dependencies>
    <dependency>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
    </dependency>
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-test</artifactId>
    </dependency>
  </dependencies>
```

**Build - Plugin Management**: adding the plugins that all sub-projects will need

```
<build>
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <plugin>
          <groupId>com.springframework.boot</groupId>
          <artifactId>spring-boot-maven-plugin</artifactId>
          <version>${spring.boot.maven.plugin.version}</version>
        </plugin>
      </plugins>
    </pluginManagement>
</build>
```
