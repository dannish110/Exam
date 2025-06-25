<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.0.0-M7</version> <configuration>
                <testFailureIgnore>true</testFailureIgnore> <parallel>classes</parallel> <threadCount>4</threadCount> <forkCount>1C</forkCount> <reuseForks>false</reuseForks> <includes>
                    <include>**/TestRunner.java</include> 
                </includes>

                <argLine>-Dcucumber.options="--plugin pretty --plugin json:target/cucumber-reports/cucumber.json --plugin html:target/cucumber-reports/cucumber.html"</argLine>
                
                </configuration>
        </plugin>

        <plugin>
            <groupId>net.masterthought</groupId>
            <artifactId>maven-cucumber-reporting</artifactId>
            <version>5.6.0</version>
            <executions>
                <execution>
                    <id>execution</id>
                    <phase>verify</phase>
                    <goals>
                        <goal>generate</goal>
                    </goals>
                    <configuration>
                        <projectName>cucumber-jvm-example</projectName>
                        <jsonFiles>
                            <param>**/*.json</param>
                        </jsonFiles>
                        <outputDirectory>${project.build.directory}/advanced-reports/cucumber-reports</outputDirectory>
                        <inputDirectory>${project.build.directory}/cucumber-reports</inputDirectory>
                        <checkBuildResult>false</checkBuildResult>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
