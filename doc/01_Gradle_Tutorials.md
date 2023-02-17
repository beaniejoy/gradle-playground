# Gradle Tutorials

- about gradle first introduction
- [gradlehero site](https://learn.tomgregory.com/courses/gradle-hero)

## :pushpin: How gradle works with java

### plugins

```groovy
plugins {
  id 'java'
}

java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(17)
    }
}
```
- Gradle Java Plugin
  - contains set of tasks
  - configures project in certain way & adds additional tasks
- [java - toolchain](https://docs.gradle.org/current/userguide/toolchains.html#toolchains)
  - A Java toolchain is a set of tools to build and run Java projects, which is usually provided by the environment via local JRE or JDK installations.


### tasks
- compile java
```shell
$ ./gradlew compileJava
```
uses java installation to compile `.java` into `.class` files  
`/build/classes/..`

- managing resources(`processResources`)
```shell
$ ./gradlew processResources
```
copies contents of `resources` directories into `build` directory  
(`/build/resources/main/`)  

- package into jar file
```shell
$ ./gradlew jar
```
`/src/main/java` & `/src/resources` > `/build/libs/app-0.0.1.jar`

- easily run tests
```shell
$ ./gradlew test
```
compiles tests, process resources, runs tests  
and creates a test report(`/build/reports/tests/test/index.html`)

- define dependencies
```groovy
dependencies {
  testImplementation 'org.junit.jupiter:junit-jupiter:5.9.1'
  implementation 'com.google.guava:guava:31.1-jre'
}
```
`implementation`: any dependencies required during compilation, execution of code  
`implementation`: similar to `implementation`, about test  
dependency configuration used to **generate classpath**
