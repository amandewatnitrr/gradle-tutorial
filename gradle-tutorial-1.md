<p align="justify">
<strong>

# Getting Started with Gradle - <img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=Gradle&logoColor=white">

![](https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/gradle11.png)

- Gradle became one of the de facto standard build tools for programming languages and ecosystems.
- It's capabilities combine conventions and built-in features to keep automation logic to a minimum while at the same time providing flexibility to fulfill customer requirements.
- This makes gradle a suitable choice for ambitious open-source and enterprise projects.
- The DevOps and continuous delivery methodologies promote a strong focus on automating the whole life cycle of a project, and that's where gradle fits right in.
- Gradle is a build tool meaning you can automate the typical tasks of a software project like compiling source code and running tests. The language used for defining the build logic in Gradle is either <img src="https://img.shields.io/badge/Groovy-4298B8?style=plastice&logo=Groovy&logoColor=white"> and <img src="https://img.shields.io/badge/Kotlin-7F52FF?style=plastice&logo=Kotlin&logoColor=white">

## What is Gradle?

- Software projects small a or large alike need a streamlined process for automating the creation and the release of it's deliverable artifacts. This process typically referred to as `Build Automation` can include compiling the source code, running different type of tests and creating binary artifact.
- Gradle is an open-source build automation tool flexible enough to define and execute instructions for different programming languages and automation tasks.
- Gradle is the primary automation tool for building Android applications, can automate the software life cycle of a Go or Python project, and produce technical documentation with the help of a markup language like Markdown or AsciiDoc.
- Therefore you can think of Gradle as a general purpose builD automation tool.

### Characteristics and Features pof Gradle

- Gradle runs on the `Java Virtual Machine` which means you need to have the `Java Development Toolkit` installed to get started.
- The Central Definition of the Automation Logic lives in the build script.
- It defines what can be achieved for a project.
- Often times the logic contained in the script is relatively small. Gradle offers a number of pre-defined plugins suited for typical project types.
- With Gradle there's no need to write everything from scratch.
- While Gradle's primary user interface is the command line, IDE support is available for the most prominent products like <img src="https://img.shields.io/badge/IntelliJ_IDEA-FFFFFF?style=plastice&logo=Jetbrains&logoColor=black">, <img src="https://img.shields.io/badge/Eclipse-2C2255?style=plastice&logo=Eclipse&logoColor=white"> and <img src="https://img.shields.io/badge/vscode-007ACC?style=plastice&logo=visualstudio&logoColor=white">.
- The above is true for continuous integration products like <img src="https://img.shields.io/badge/Jenkins-D24939?style=plastice&logo=Jenkins&logoColor=white">, <img src="https://img.shields.io/badge/Teamcity-FFFFFF?style=plastice&logo=Teamcity&logoColor=black"> and <img src="https://img.shields.io/badge/Github_Actions-2088FF?style=plastice&logo=githubactions&logoColor=white">.
- To summarize, Gradle is an automation tool well-suited for building wide range of project types, for example microservices or large range enterprise projects comprised of many sub-components.

## Basic Gradle Terminologies

<img width="50%" align="right" src="https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/services1.gif">

- At the core of every gradle build lies a so-called project.
- The Project defines the capabilities and boundaries of a software component.
- The actual work of the build can be defined with a so-called task.
- The task defines the step-by-step automation instructions.
- Let's try to do some basic stuff with gradle now.

```groovy

    task helloworld{
        doLast{
            println "Hello World"
        }
    }
```

```BASH
00000000@LAPPYID MINGW64 ~/tech/gradle/test (master)
$ gradle helloworld

> Task :helloworld
Hello World

BUILD SUCCESSFUL in 913ms
1 actionable task: 1 executed
```

</strong>
</p>
