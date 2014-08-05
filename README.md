# Spring Integration Version Management

----

## Superceded
Please note that this project has effectively been superceeded by an official
Spring project.

    <dependency>
	    <groupId>org.springframework.integration</groupId>
	    <artifactId>spring-integration-bom</artifactId>
	    <version>4.0.x.RELEASE</version>
    </dependency>

----

If you've ever created a moderately complex project which uses Spring, you've
likely come across issues having to manage versions of Spring transitive
dependencies.

Your project uses Spring Integration 3.0.1.RELEASE, but something else you're
depending on imports some otherwise unused Spring Integration module, at
3.0.0.RELEASE.

You end up declaring a `dependencyManagement` entry for just about every Spring
Integration module there is, to ensure that anything you bring in uses the
correct version.

Enter `spring-integration-version`

```xml
<project>
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>com.github.ptomli.spring-integration-version</groupId>
        <artifactId>spring-integration-version</artifactId>
        <version>3.0.1.RELEASE</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
</project>
```

`spring-integration-version` simply declares a `dependencyManagement` entry for
each Spring Integration module, at its own `project.version`. So,
`spring-integration-version` `3.0.1.RELEASE` will result in any Spring
Integration transitive dependency being imported at `3.0.1.RELEASE`. Done,
finished and klaar!

There are companion projects to handle other SpringSource project versions, such
as
[spring-version](https://github.com/ptomli/spring-version)
and
[spring-security-version](https://github.com/ptomli/spring-security-version)
