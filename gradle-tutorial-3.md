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
- Any logic that should eb executed during the execution phase should be defined as part of the `doFirst` and `doLast` action logic.

</strong>
</p>