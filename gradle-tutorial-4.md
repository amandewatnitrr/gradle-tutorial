<p align="justify">
<strong>

# Gradle Essentials - <img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=Gradle&logoColor=white">

![](https://github.com/amandewatnitrr/gradle-tutorial/blob/master/imgs/gradle19.png)

## Domain Objects in Memory

- In previous lesson, we discussed Gradle builds a Directed Acyclic Graph for tasks and dependencies b/w them.
- The Representation of those tasks as objects in memory is called Domain Objects. Gradle makes available to end users of a build.
- Domain Objects can be cleared from a build script, inspected and modified. That's a feature that many other build tools do not provide.

### Important Domain Objects

- Every invocation of a greater build is represented by a domain object called `Gradle`.
- This domain object has knowledge about the project hierarchy in a single project, or multi-project build provides pointers to higher level properties of a build.
  - For example, the Gradle user home directory or the USe Gradle Version and can register callback logic to react to certain events in the build.
- The Project Domain Object serves as the main entry point of the build.
- It provides methods for making the whole hierarchy of domain objects.
  - For example, you could ask for the reference to the Gradle Instance, register new tasks, or get a modified typical environmental properties like the build output directory.
- The Task Domain Object performs the actual work at runtime.
- From a project we can register as many tasks as we'd like.
- Every task can declare test dependencies.
- In most cases, tasks define at least one action.
- Gradle executes those actions in order of declaration.
- It's important to mention that you can define doFirst and doLast Actions.
- `doFirst` actions happen before `doLast` actions.
- Every plugin we apply to a project is represented as a Plugin Domain Object.
- A Plugin has full access to the project it works on and therefore can access other domain objects by name or by type and modify them as necessary.

## Using the Gradle Documentation and Gradle User Guide

- Explains Grdle on the Conceptional Level
- Helps with Understanding Mechanics and Capabilities
- It is important to build the mental bridge b/w a build script and the relevant documentation. If not understood properly, copy pasting the code from the internet becomes the norm without understanding the why and how.
- You can also find out hands-on practical portion in the user manual, so called Gradle Guides.
- The Guides implement a tutorial style approach that helps with understanding specific aspects of the build tool by example.
- For better understanding of the Gradle DSL, gain basic knowledge of the language you're using.
- When using the Groovy DSL, ou should at least be comfortable with Groovy Syntax.
- The Gradle Build Language Reference documents all domain Objects plus their public properties and methods.
- Gradle itself is built with the Java Language, you can zoom into the API even further by looking at the JavaDocs.

</strong>
</p>
