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
  - <img src="https://shields.io/badge/Initialisation-phase-00cc44?logo=gradle&style=plastic">
  - <img src="https://shields.io/badge/Configuration-phase-ffff00?logo=gradle&style=plastic">
  - <img src="https://shields.io/badge/Execution-phase-ff0000?logo=gradle&style=plastic">

- 

</strong>
</p>