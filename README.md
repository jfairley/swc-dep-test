# swc-dep-test

For Artifactory support, please use this sample project to debug the Unauthorized access errors for .swc files.

## Maven

Using Maven 3.3.3

```
mvn package -X
```

See logs: [maven.log](maven.log)


## Gradle

Using gradle 2.6

With gradle it is very easy to specify the order that depedencies are resolved. Interestingly, I found that the order matters.

Pulling from the same local repository, NimbusCommonLibs can be accessed successfully only when it is not the first .swc file.

#### Failure:
```
rm -rf ~/.gradle/caches  ## clear downloaded artifacts
gradle -b build.nimbusFirst.gradle build --debug --stacktrace
```

See logs:
- [gradle.nimbusFirst.stdout.log](gradle.nimbusFirst.stdout.log)
- [gradle.nimbusFirst.stderr.log](gradle.nimbusFirst.stderr.log)

#### Success:
```
rm -rf ~/.gradle/caches  ## clear downloaded artifacts
gradle -b build.nimbusLast.gradle build --debug --stacktrace
```

See logs:
- [gradle.nimbusLast.stdout.log](gradle.nimbusLast.stdout.log)
- [gradle.nimbusLast.stderr.log](gradle.nimbusLast.stderr.log)
