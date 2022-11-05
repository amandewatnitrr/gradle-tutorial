<p align="justify">
<strong>

# Gradle Essentials - <img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=Gradle&logoColor=white">

![](https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/gradle3.png)

- Let's now understand the typical file and directory structure of a gradle projcet.
- We already discussed the purpose of the `build.gradle` file, which is the build script. It contains the build logic of the project.
- The file resides in the root directory of the project.
- Gradle does prescribe how to structure the source files of your project. In pactice we may find many projects that break up the code into multiple components for mantainary reasons, and to enforce sepration of concerns.
- Gradle can model each of those components as project, including dependencies b/w each other.
- Per Project, you can define a `build.gradle` file that contains build logic for managing a component.
- Gradle calls to setup a multi-project build.

<img src="https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/code-example-4.png">

- In gradle land you define the multi-project build by creating a `settings.gradle` file in the root directory of the project.
- Within the file we can spell out the projects that participate in a build enter names.
- We only dealt with a single project, so there was no need to spell out other components.
- Gradle automatically derives the name of the project from he directory that contains the `build.gradle` file.
- The build in task projects can provide us with this information.
- Let's declare a `settings.gradle` file and use it to declare a more appropriate name, say `hello-world`.
-

<img src="https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/code-example-5.png">

- If the project would define more than a single project, the terminal output of the task would render a tree hierarchy.
- For now we won't go into more details on multi-project builds refer to the Gradle User Guide for more information.
- Lastly, we want to touch on the file `gradle.properties`.
- We can create the file in root directory of the project to define runtime options for your build or as a means to externalize custom key value pairs usable in the `build.gradle` file.
- Let's learn about it through an example:
  - You might have noticed that build output in gradle is not very noisy.
  - We can provide more information bu changing the log level for console output to  info with the option, `org.gradle.logging.level=info`. For that we are going to edit the `gradle.properties` file.
  - Additionally, we also want to provide a version of the project.
  - Here, we are declaring the custom key value pair `version=1.0.0`.
  - We can access this property in the build script by key, we will modify the `println` statement to also render the version. Executing the `hello-world` now shows a change of behavior.
  - If you happen to find certain useful properties for other projects, they can also define the `gradle.properties` file under user `home/.gradle` which is referred to the gradloe user home directory. This will make the property available to all gradle projects run on the machine.

    ```bash
    000000000@LAPPY_CODE MINGW64 ~/tech/gradle/test (master)
    $ gradle helloworld
    Initialized native services in: C:\Users\000000000\.gradle\native
    Initialized jansi services in: C:\Users\000000000\.gradle\native
    The client will now receive all logging from the daemon (pid: 15500). The daemon log file: C:\Users\000000000\.gradle\daemon\7.5.1\daemon-15500.out.log
    Starting 8th build in daemon [uptime: 3 hrs 18 mins 58.686 secs, performance: 100%, non-heap usage: 18% of 256 MiB]
    Using 8 worker leases.
    Now considering [C:\Users\000000000\tech\gradle\test] as hierarchies to watch
    Watching the file system is configured to be enabled if available
    File system watching is active
    Starting Build
    Settings evaluated using settings file 'C:\Users\000000000\tech\gradle\test\settings.gradle'.
    Projects loaded. Root project using build file 'C:\Users\000000000\tech\gradle\test\build.gradle'.
    Included projects: [root project 'hello-world']

    > Configure project :
    Evaluating root project 'hello-world' using build file 'C:\Users\000000000\tech\gradle\test\build.gradle'.
    Compiling build file 'C:\Users\000000000\tech\gradle\test\build.gradle' using SubsetScriptTransformer.
    Compiling build file 'C:\Users\000000000\tech\gradle\test\build.gradle' using BuildScriptTransformer.
    All projects evaluated.
    Task name matched 'helloworld'
    Selected primary task 'helloworld' from project :
    Tasks to be executed: [task ':helloworld']
    Tasks that were excluded: []
    Resolve mutations for :helloworld (Thread[Execution worker,5,main]) started.
    Resolve mutations for :helloworld (Thread[Execution worker,5,main]) completed. Took 0.0 secs.
    :helloworld (Thread[Execution worker Thread 2,5,main]) started.

    > Task :helloworld
    Caching disabled for task ':helloworld' because:
    Build cache is disabled
    Task ':helloworld' is not up-to-date because:
    Task has not declared any outputs despite executing actions.
    Hello World -1.0.0
    :helloworld (Thread[Execution worker Thread 2,5,main]) completed. Took 0.019 secs.

    BUILD SUCCESSFUL in 1s
    1 actionable task: 1 executed
    Watched directory hierarchies: [C:\Users\000000000\tech\gradle\test]
    ```

## Defining and Configuring a Task

<img width="60%" align="left" src="https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/gradle18.png">

- A task defines executable unit of work.
- The logic to be executed is defined in one or many actions. We've seen the very simple task in action.
- It simply rendered a message to the terminal.
- Gradle calls those tasks `ad hoc tasks` .
- As soon as we dive deeper, you'll find that gradle also lets you specify a type.
- Let's quickly compare both the approaches.
<br><br>
### Ad Hoc Tasks

- `Ad hoc` tasks are a good fit for one-off action implementations.
- We did not need to define an explicit type as they automatically use the default implementation. o the task interface.
- That default implementation is called `Default Task`.

</strong>
</p>
