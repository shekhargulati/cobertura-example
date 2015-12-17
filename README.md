Multi-module Maven Cobertura Project
-------

To build the project just run

```bash
mvn clean install
```

The project will fail to build as code coverage is below 85%. Cobertura plugin is defined in the root pom.xml as shown below.

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.codehaus.mojo</groupId>
            <artifactId>cobertura-maven-plugin</artifactId>
            <version>2.7</version>
            <configuration>
                <check>
                    <branchRate>85</branchRate>
                    <lineRate>85</lineRate>
                    <haltOnFailure>true</haltOnFailure>
                    <totalBranchRate>85</totalBranchRate>
                    <totalLineRate>85</totalLineRate>
                    <packageLineRate>85</packageLineRate>
                    <packageBranchRate>85</packageBranchRate>
                </check>
                <formats>
                    <format>html</format>
                    <format>xml</format>
                </formats>
                <aggregate>true</aggregate>
            </configuration>
            <executions>
                <execution>
                    <phase>post-integration-test</phase>
                    <goals>
                        <goal>check</goal>
                        <goal>cobertura</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

All the child project inherits uses the configuration.