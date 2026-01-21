# SimpleCommandInteractionPlugin

A Hytale server plugin that adds a simple block interaction capable of executing server commands.

This repository is a fork of the original plugin by wolfifurr
- [Github](https://github.com/wolfifurr/SimpleCommandInteractionPlugin)
- [Curseforge](https://www.curseforge.com/hytale/mods/simplecommandinteraction)

Updates:
- build with modern Gradle
- use Java toolchains cleanly
- eventually add new plugin features

---

## Requirements

### Required
- **Java 25 JDK** (for compilation)
- **Java 21+ JDK** (for Gradle + IDE runtime)
- **HytaleServer.jar** (current version: `2026.01.17-4b0f30090`)
  - via hytale-downloader link (must be logged into [your hytale account](https://www.hytale.com))

> The Hytale server jar is **not** included in this repository and must be provided locally.

---

## Repository Structure

This project intentionally follows Gradle’s two-layer configuration model:

| Location | Purpose |
|--------|--------|
| `gradle.properties` (repo root) | Project defaults (portable) |
| `~/.gradle/gradle.properties` | Machine-specific overrides |

Create a customized ~/.gradle/gradle.properties if needed

---

## Quick Start

### 1. Install Java JDKs and Gradle

This project uses two versions of Java:
- [Java 21](https://adoptium.net/temurin/releases?version=21&os=any&arch=any) for Gradle and IDE tooling (due to maturity)
- [Java 25](https://adoptium.net/temurin/releases?version=25&os=any&arch=any) to compile the plugin (required by Hytale)
- The gradle config handles the versioning so update that if you prefer to use only Java 25

This project also uses [Gradle 8.14.3](https://gradle.org/releases/#8.14.3)

Ensure `gradle` is on your `$PATH`.

### 1b. Configure local `~/.gradle/gradle.properties` (if needed)

Depending on your Java installation setup you may need to override the `gradle.properties`. To do that, create `~/.gradle/gradle.properties` and edit it accordingly.  
> your customized `gradle.properties` file needs to be placed in your `$HOME` directory, **NOT** in the project's `.gradle` folder.

example `~/.gradle/gradle.properties` file

```bash
org.gradle.java.installations.paths=C:/path/to/jdk-25
org.gradle.java.installations.auto-detect=false
org.gradle.java.installations.auto-download=false
```

### 2. Clone the repository

```bash
git clone https://github.com/boylecraft/SimpleCommandInteractionPlugin.git
cd SimpleCommandInteractionPlugin
```

### 3. Copy `HytaleServer.jar` to `./libs/`

- Create the `libs` folder if it doesn't exist in your project
- Download the correct version of the Hytale Server from [your hytale account](https://www.hytale.com)
- Unzip and copy `./Server/HytaleServer.jar` to `./libs`

### 4. Build the plugin:

- Run `./gradlew clean build`
- The plugin should compile and be created in `./build/libs`

> To change the version of the plugin, edit the `version` attribute in `build.gradle.kts`.

### Optional VSCode Stuff

Edit your `Open User Settings (JSON)` (via `Ctrl + Shift + P`)

```json
{
  "java.jdt.ls.java.home": "E:\\dev\\java\\jdk-21.0.9+10",
  "java.import.gradle.java.home": "E:\\dev\\java\\jdk-21.0.9+10"
}
```

- add a `.vscode/tasks.json` with the following:
```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Build Plugin",
      "type": "shell",
      "command": "./gradlew build",
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "problemMatcher": "$javac"
    }
  ]
}
```
- Now you can build the plugin inside VSCode via: `Ctrl + Shift + B`

### Optional VSCode extensions

For Java development in VSCode you might find the following plugins useful
- [Java extension pack](https://marketplace.visualstudio.com/items?itemName=walkme.Java-extension-pack)
- [Gradle for Java](https://github.com/microsoft/vscode-gradle)
- [FWCD Kotlin](https://github.com/fwcd/vscode-kotlin)
