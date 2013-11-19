# Spring Integration Version Management

If you've ever created a moderately complex project which uses Spring, you've
likely come across issues having to manage versions of Spring transitive
dependencies.

Your project uses Spring Integration 2.2.5.RELEASE, but something else you're
depending on imports some otherwise unused Spring Integration module, at
2.0.1.RELEASE.

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
        <version>2.2.5.RELEASE</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
</project>
```

`spring-integration-version` simply declares a `dependencyManagement` entry for
each Spring Integration module, at its own `project.version`. So,
`spring-integration-version` `2.2.5.RELEASE` will result in any Spring
Integration transitive dependency being imported at `2.2.5.RELEASE`. Done,
finished and klaar!

There are companion projects to handle other SpringSource project versions, such
as
[spring-version](https://github.com/ptomli/spring-version)
and
[spring-security-version](https://github.com/ptomli/spring-security-version)
