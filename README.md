# Maven Download Plugin
This is a plugin meant to help maven user to download different files on different protocol in part of maven build.

## Enable 

```xml
<pluginRepository>
	<id>sonatype-public-repository</id>
	<url>https://oss.sonatype.org/content/groups/public</url>
	<snapshots>
		<enabled>true</enabled>
	</snapshots>
	<releases>
		<enabled>true</enabled>
	</releases>
</pluginRepository>
````

You can use some alternative repositories. See https://docs.sonatype.org/display/Repository/Sonatype+OSS+Maven+Repository+Usage+Guide#SonatypeOSSMavenRepositoryUsageGuide-4.MavenRepositories for details.

## Basic Usage

Examples have been created and deployed into the plugin documentation which can be consulted [http://maven-download-plugin.googlecode.com/svn/site/index.html here] and [http://maven-download-plugin.googlecode.com/svn/site/snapshot/index.html here for snapshot doc].

Here is a list of the basic usage of each of the goal of the plugin.

### "Artifact" goal
Meant to be used from anywhere on the system to download an artifact at a specific location.  Does not need a pom file to be run and can be used directly from the command line.
Can be an alternative to [maven-dependency-plugin:get](http://maven.apache.org/plugins/maven-dependency-plugin/get-mojo.html) or [maven-depdendency-plugin:unpack](http://maven.apache.org/plugins/maven-dependency-plugin/unpack-mojo.html maven-dependency-plugin:unpack) mojoes.


```
mvn com.googlecode.maven-download-plugin:maven-download-plugin:artifact -DgroupId=com.googlecode -DartifactId=maven-download-plugin -Dversion=0.1 -DoutputDirectory=temp
```

### "WGet" goal
This is meant to provide the necessary tooling for downloading anything in your Maven build without having to use Ant scripts.
It provides caching and signature verification.
```xml
<plugin>
	<groupId>com.googlecode.maven-download-plugin</groupId>
	<artifactId>maven-download-plugin</artifactId>
	<version>1.0.0</version>
	<executions>
		<execution>
			<id>install-jbpm</id>
			<phase>pre-integration-test</phase>
			<goals>
				<goal>wget</goal>
			</goals>
			<configuration>
				<url>http://downloads.sourceforge.net/project/jbpm/jBPM%203/jbpm-3.1.4/jbpm-3.1.4.zip</url>
				<unpack>true</unpack>
				<outputDirectory>${project.build.directory}/jbpm-3.1.4</outputDirectory>
				<md5>df65b5642f33676313ebe4d5b69a3fff</md5>
			</configuration>
		</execution>
	</executions>
</plugin>
```

# Help

To get basic plugin help, type in the command : 
```
mvn help:describe -Dplugin=com.googlecode.maven-download-plugin:maven-download-plugin
```

To get a more detailed help, type command : 
```
mvn help:describe -Dplugin=com.googlecode.maven-download-plugin:maven-download-plugin -Ddetail
```

See also [generated documentation pages](https://raw.github.com/mickaelistria/maven-download-plugin/docsite/docsite/1.0.0/index.html).