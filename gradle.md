# Gradle

## Config

Project build configuration is defined by `build.gradle`, written using the Groovy or Kotlin DSL. It's important to note that the `build.gradle` is a script, allowing customization through code modifications.

### Example `build.gradle`

```
plugins {
	// Sets up the project structure (ie src/main/java, etc) and 
	// adds standard tasks
    id 'java'
    
    // Sets up the project as an application, allowing a main class
    // to be defined. Also uses the 'java' plugin, so there is 
    // no need to define both, but both are here for demonstration.
    id 'application'
    
    // Adds lombok annotations and features
    id 'io.freefair.lombok' version '8.3'
    
    // Add checkstyle for the project to adhere to a specified
    // coding standard.
    id 'checkstyle'
    
    // Static code analyzer
    id 'pmd'
}

group = 'com.ebonyandirony'
version = '1.0-SNAPSHOT'

jar {
	// Adds a manifest to the created jar so the jar command
	// knows which main class to run.
    manifest {
        attributes 'Main-Class': 'com.ebonyandirony.chess.ChessMain'
    }
}

application {
    mainClass = 'com.ebonyandirony.chess.ChessMain'
}

// Some default rulesets for PMD. They can be found at
// https://github.com/pmd/pmd/blob/master/pmd-java/
pmd {
    ruleSets = ['category/java/bestpractices.xml', 'category/java/codestyle.xml']
}

repositories {
    mavenCentral()
}

// This config uses version cataloging to define dependencies
dependencies {
    testImplementation platform(libs.junit.bom.core)
    testImplementation libs.junit.jupiter
    testImplementation libs.junit.jupiter.engine
    testImplementation libs.assertj.core
    testImplementation libs.mocktio.core
}

test {
    useJUnitPlatform()
}
```

## Wrapper scripts

Developers should use the wrapper scripts `gradlew` (Linux and Mac) and `gradlew.bat` to run Gradle tasks rather than the locally installed version of Gradle. These scripts define which version of Gradle the project requires, downloading the correct version and caching it in the users `~/.gradle` directory. The wrappers should be included in version control.

## Version catalog

Gradle version catalogs simplify the management of dependencies within build scripts. Instead of directly including dependencies in a project's `build.gradle`, you add them to a centralized configuration file named `libs.versions.toml`, located in the `gradle` directory of your project.

### Example toml

```
[versions]
assertj = "3.24.2"
mockito = "3.+"
junit-jupiter = "5.9.2"

[libraries]
mocktio-core = { module = "org.mockito:mockito-core", version.ref = "mockito" }
assertj-core = { module = "org.assertj:assertj-core", version.ref = "assertj" }
junit-bom-core = { module = "org.junit:junit-bom", version.ref = "junit-jupiter" }
junit-jupiter-engine = { module = "org.junit.jupiter:junit-jupiter-engine", version.ref = "junit-jupiter" }
junit-jupiter = { module = "org.junit.jupiter:junit-jupiter", version.ref = "junit-jupiter" }
```

### Reference the dependencies within `build.gradle`

```
dependencies {
    testImplementation platform(libs.junit.bom.core)
    testImplementation libs.junit.jupiter
    testImplementation libs.junit.jupiter.engine
    testImplementation libs.assertj.core
    testImplementation libs.mocktio.core
}
```
