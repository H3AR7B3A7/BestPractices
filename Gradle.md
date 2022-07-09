# Gradle

- Convention based
- Highly configurable
- DSL (Domain Specific Language)
  - Groovy
  - Kotlin
- Support for multi-project builds
- Easily customizable
- Builds many languages
- Dependency management

## Install

- Manually
  - Download [binary-only](https://gradle.org/releases/) files
  - Unzip
  - Set environment variable:
    > export PATH=$PATH:~/gradle-7.4.2/bin
  - Test
    > gradle -v
- SDKMAN
  > sdk install gradle
- Homebrew
  > brew install gradle

### Gradle Wrapper

We can also use gradle to install a gradle wrapper
> gradle wrapper

We can then run gradle tasks using the wrapper.
> ./gradlew build

*The wrapper will download a version of gradle as a jar in **./gradle/wrapper**.
This way we can specify within the task exactly which version of Gradle should be used.*

## Build Script Language

- Groovy DSL
  - Older
  - A lot of examples and help
  - Slightly cleaner
- Kotlin
  - Newer
  - Typed
  - Help in IDE

### Examples

#### Groovy

```groovy
task 'hello' {
  doLast {
    println "Hello Gradle"
  }
}
```

#### Kotlin

```kotlin
tasks.register("hello") {
    doLast {
        println("Hello Gradle")
    }
}
```

## Tasks

- build
- clean
- ...

*Can be run on commandline or in the IDE.*

## Version 7.3

