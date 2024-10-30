---
title: Installation (for developers)
breadcrumb: Dev Installation
layout: cca_wiki
---

Getting Cardinal Components into your workspace is a matter of adding a few lines in your Gradle buildscript (`build.gradle` file).
Once you get to publishing your mod, you have two options:

1. Have users install the library from a mod distribution platform like [Modrinth](https://modrinth.com/mod/cardinal-components-api).
   Most launchers can install it automatically if you correctly declare the dependency when publishing your mod.
2. Include the library in your own builds using the [Jar-in-Jar](https://fabricmc.net/wiki/tutorial:loader04x#nested_jars)
   mechanism provided by the Fabric toolchain. This eliminates the need for manual install, at the cost of inflated modpack size when several mods bundle it at once.

*The following instructions are valid for versions 4.1 and up. For previous versions, refer to [the table below](#previous-maven-coordinates).*

{% buildscript [cca:K01OU20C] %}
[- groovy -]
`gradle.properties`:
```properties
cca_version = <VERSION>
```

`build.gradle`:
```gradle
repositories {
    maven {
        name = "Ladysnake Mods"
        url = 'https://maven.ladysnake.org/releases'
    }
}

dependencies {
    // Replace modImplementation with modApi if you expose components in your own API
    modImplementation "<MAVEN_GROUP>.cardinal-components-api:cardinal-components-base:${project.cca_version}"
    modImplementation "<MAVEN_GROUP>.cardinal-components-api:cardinal-components-<MODULE>:${project.cca_version}"
    // Copy the following only if you want to bundle Cardinal Components API as a Jar-in-Jar dependency
    // (otherwise, you should configure the dependency on Modrinth/Curseforge)
    include "<MAVEN_GROUP>.cardinal-components-api:cardinal-components-base:${project.cca_version}"
    include "<MAVEN_GROUP>.cardinal-components-api:cardinal-components-<MODULE>:${project.cca_version}"
}
```

[- kts -]
`gradle.properties`:
```properties
cca_version = <VERSION>
```

`build.gradle.kts`:
```kotlin
repositories {
    maven {
        name = "Ladysnake Mods"
        url = "https://maven.ladysnake.org/releases"
    }
}

dependencies {
    val ccaVersion = property("cca_version") as String
    // Replace modImplementation with modApi if you expose components in your own API
    modImplementation("<MAVEN_GROUP>.cardinal-components-api:cardinal-components-base:$ccaVersion")
    modImplementation("<MAVEN_GROUP>.cardinal-components-api:cardinal-components-<MODULE>:$ccaVersion")
    // Copy the following only if you want to bundle Cardinal Components API as a Jar-in-Jar dependency
    // (otherwise, you should configure the dependency on Modrinth/Curseforge)
    include("<MAVEN_GROUP>.cardinal-components-api:cardinal-components-base:$ccaVersion")
    include("<MAVEN_GROUP>.cardinal-components-api:cardinal-components-<MODULE>:$ccaVersion")
}
```

[- catalogue -]
`libs.versions.toml`:
```toml
[versions]
cca = '<VERSION>'

[libraries]
cca-base = { module = "<MAVEN_GROUP>.cardinal-components-api:cardinal-components-base", version.ref = "cca" }
cca-<MODULE> = { module = "<MAVEN_GROUP>.cardinal-components-api:cardinal-components-<MODULE>", version.ref = "cca" }

[bundles]
cca = [ "cca-base", "cca-<MODULE>" ]
```

`build.gradle` or `build.gradle.kts`:
```kotlin
repositories {
    maven {
        name = "Ladysnake Mods"
        url = "https://maven.ladysnake.org/releases"
    }
}

dependencies {
    // Replace modImplementation with modApi if you expose components in your own API
    modImplementation(libs.bundles.cca)
    // Copy the following only if you want to bundle Cardinal Components API as a Jar-in-Jar dependency
    // (otherwise, you should configure the dependency on Modrinth/Curseforge)
    include(libs.bundles.cca)
}
```
{% endbuildscript %}

### Previous maven coordinates

| CCA Version | MC Version | Maven Group                                   | Additional notes            |
|-------------|------------|-----------------------------------------------|-----------------------------|
| 1.0         | 1.14       | com.github.NerdHubMC                          | Single artifact (no module) |
| 2.0         | 1.14.3     | com.github.NerdHubMC.Cardinal-Components-API  | First modularized version   |
| 2.4.0       | 1.16       | io.github.onyxstudios.Cardinal-Components-API |                             |
| 4.1.0       | 1.18       | dev.onyxstudios.cardinal-components-api       | Lowercased group            |
| 6.0.0       | 1.20.5     | org.ladysnake.cardinal-components-api         |                             |
{:.table-striped.table-figure}

## Ladysnake Reposilite

The current recommended way of getting the latest releases of Cardinal Components API is to use the Ladysnake maven repository :

```gradle
repositories {
    maven {
        name = "Ladysnake Mods"
        url = 'https://maven.ladysnake.org/releases'
    }
}
```

This maven repository contains binaries for every version since 3.0.0-21w06a.

## Jitpack

[Jitpack](https://jitpack.io#OnyxStudios/Cardinal-Components-API) is a simple alternative to dedicated mavens,
building GitHub repositories on demand. It can be used to get any version of Cardinal Components,
including snapshots of development branches. Note however that it tends to slow down your builds,
and that it often times out the first time it builds an artefact (just restart the build when that happens).
Further use information can be found on the website itself.

```gradle
repositories {
    maven {
        name = "Jitpack"
        url = "https://jitpack.io"
    }
}
```

## Curseforge

CurseForge is mostly a platform for distributing mods to users.
Although not recommended, it can be used as a maven repository by following [the instructions on the website](https://authors.curseforge.com/knowledge-base/projects/529-api).
A slightly better way to do it is using the [CurseMaven Gradle plugin](https://github.com/Wyn-Price/CurseMaven).

You are however encouraged to declare [Cardinal Components API](https://www.curseforge.com/minecraft/mc-mods/cardinal-components-api)
as an *embedded library* of your project, for documentation purposes and to make it simpler for users to report issues to the right repository.

## Modrinth

Modrinth is also a platform for distributing mods to users, which can also be used as a maven repository by following [the instructions on their website](https://docs.modrinth.com/docs/tutorials/maven/).

Same as with Curseforge, you are encouraged to declare [Cardinal Components API](https://modrinth.com/mod/cardinal-components-api/) as an "Embedded" dependency.

## Historical mavens

These mavens may be referenced in older buildscripts, but cannot be used anymore.

### Ladysnake artifactory

```gradle
repositories {
    maven {
        name = "Ladysnake Mods"
        url = 'https://ladysnake.jfrog.io/artifactory/mods'
    }
}
```

This maven repository contained binaries for every version between 3.0.0-21w06a and 5.2.1.
Due to JFrog Artifactory's free tier shutting down, it is now unavailable.

### Ladysnake bintray

```gradle
repositories {
    maven {
        name = "Ladysnake Libs"
        url = 'https://dl.bintray.com/ladysnake/libs'
    }
}
```

This maven repository contained binaries for every version between 2.3.5 (MC 1.15) and 2.7.11 (MC 1.16).
Due to bintray shutting down, it is now unavailable.

### OnyxStudios Maven

The former official maven, that contains versions up to 2.3.0:

```gradle
repositories {
    maven {
        name = "OnyxStudios"
        url = "https://maven.abusedmaster.xyz"
    }
}
```
