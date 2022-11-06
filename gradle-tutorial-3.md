<p align="justify">
<strong>

# Gradle Essentials - <img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=Gradle&logoColor=white">

![](https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/gradle12.png)

## Build Lifecycle Phases

- Gradle builds a complete directed acyclic graph before any task is executed.
- Your build script is responsible for defining those tasks and their dependencies.
- Whenever a build is invoked by running the Gradle executable, the runtime will evaluate the instructions of the build script, create and configure the tasks and finally execute them in the correct order.
- Gradle executes this process in three distinct phases, the initialization phase, the configuration phase and the execution phase.
- Knowing the implications of those phases is extremely important for understanding what part of the build script is evaluated and when.
- Lifecycle Phases are as follows:
  - <img src="https://shields.io/badge/Initialisation-Phase-00cc44?logo=gradle&style=plastic">
  - <img src="https://shields.io/badge/Configuration-Phase-ffff00?logo=gradle&style=plastic">
  - <img src="https://shields.io/badge/Execution-Phase-ff0000?logo=gradle&style=plastic">

- Let's discuss each phase one by one:

  - Initialization Phase - <img src="https://shields.io/badge/Initialisation-Phase-00cc44?logo=gradle&style=for-the-badge">

    - The initialization phase evaluates the settings file.
    - This file contains the information about the projects that should participate in the build.
    - A settings file can exist for a single and multi-project builds.
    - You will find the file more commonly used in a multi-project build.
    - We also have seen previously, in this guide that we can also provide custom names for the projects.
  
  - Configuration Phase - <img src="https://shields.io/badge/Configuration-Phase-ffff00?logo=gradle&style=for-the-badge">

    - The Configuration Phase parses and evaluates the build logic specified in one or many build scripts.
    - Each project can define a distinct build script but doesn't nessecarily have to.
    - It's important to understand that all code in a build script is exercised not wrapped, into a callback function.
    - For example, during the configuration phase, task actions are not executed, tasks are only configured.
    - Configuration counts as assigning values to properties or calling task methods exposed by it's API.
    - Performance is critical, make sure that the code you define does not necessarily execute expensive logic as it will contribute to the time it takes befpore task actions can be run.

  - Execution Phase - <img src="https://shields.io/badge/Execution-Phase-ff0000?logo=gradle&style=for-the-badge">

    - The Execution Phase looks at the (DAG)-Directed Acyclic Graph that was built at memory and executes every task action in the correct order.
    - This is where the real work actually happens.
    - The life cycle phases are a common source of confusion for new users to the Gradle build tool.
    - Make sure to define the logic in right place.

- To summarize, Configuration code configures the project and it's tasks. The logic needs to be defined outside of the task actions.
- Any logic that should be executed during the execution phase should be defined as part of the `doFirst` and `doLast` action logic.

## Applying reusable functionality with Plugins

<img src="https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/gradle15.png">

- Every gradle build definition starts with a build script. The more you work on different build automation projects, the more you will notice that certain build code is similar or even the same. To avoid having to copy/paste build code from project to project, Gradle introduced the concept of so-called plugin.
- There are 2 types of plugins:
  - <img src="https://shields.io/badge/Script-Plugins-00cc44?logo=gradle&style=plastic">

    - A Script Plugin is just another build script that can be included into your main `build.gradle` file.
    - The Primary reason for wanting to use the script plugin is to split up the build logic and make it more maintainable.

  - <img src="https://shields.io/badge/Binary-Plugins-ffff00?logo=gradle&style=plastic">

    - Binary Plugins are meant for more complex logic bundled into a JAR File.
    - The reason being that they can reuse the functionality across multiple self-contained software projects, and those software projects usually live in different version control repositories.

- Let's have a look at an example for Script Plugin:

  - In this scenario, we decided to externalize the build logic into script plugin that deals with creating an archive for set of files. Well let's have a look at the `build.gradle` file here.
  - We are working on the same copy task and zip task, so makie sure you have the exercise file available.
  - So, in the `archive.gradle` file, we have defined a task called `createZip` that depends on the `copy` task.
  - We don't have the tasks directly written in the `build.gradle` file, but we are calling the `apply from` method and passing the path to the `archive.gradle` file.
  - `build.gradle`

    ```groovy
        apply from: "archiving.gradle" // This is a Script Plugin.
    ```

    `archiving.gradle`

    ```groovy
        task copydocs(type: Copy)
            {
                from "src"
                into "build/docs"
                include "**/*md"
                includeEmptyDirs = false
            }

        task createZip(type: Zip)
            {
                from "build/docs"
                archiveFileName = "docs.zip"
                destinationDirectory = file("build/dist")
                dependsOn copydocs
            }
    ```

    `OUTPUT`

    ```bash
    000000000@LAPPY_CODE MINGW64 ~/tech/gradle/archiving-project (master)
    $ gradle createZip
    Starting a Gradle Daemon (subsequent builds will be faster)

    BUILD SUCCESSFUL in 11s
    2 actionable tasks: 2 executed
    ```

- Now let's have a look at examples for Binary Plugins:
  - Bianry Plugins are available as a part of Gradle Distribution.
  - They are also called `Core Plugins`, but there are also some community plugins out there, which are available on the Gradle Plugin Portal.
  - For this scenario, we decide to user the so-called base plugin.
  - The base plugin provides tasks and conventions common to most projects.
  - `build.gradle`

    ```groovy
        apply from: "archiving.gradle"
    ```

    `archiving.gradle`

    ```groovy
        apply plugin: "base"

        task copydocs(type: Copy)
            {
                from "src"
                into "build/docs"
                include "**/*md"
                includeEmptyDirs = false
            }

        task createZip(type: Zip)
            {
                from "build/docs"
                dependsOn copydocs
            }
    ```

    `OUTPUT`

    ```bash
    000000000@LAPPY_CODE MINGW64 ~/tech/gradle/archiving-project-binary_plugin (master)
    $ gradle createZip

    BUILD SUCCESSFUL in 2s
    2 actionable tasks: 2 executed
    ```

  - Now we can write and distribute our own binary plugins, but this topic goes beyond the scope of this guide.

</strong>
</p>
