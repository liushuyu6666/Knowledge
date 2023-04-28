# Overview
This section provides a summary and supplements to the `Java Launcher`'s class-finding process, based on
[The Oracle official website](https://docs.oracle.com/javase/8/docs/technotes/tools/findingclasses.html).

# Sharing
How different projects sharing different libraries?
## `IntelliJ IDEA`
The bootstrap libraries in Java, which includes the standard class libraries `java.lang`, `java.util`, `java.io` and JVM runtime components, are loaded automatically by the JVM when executing a Java program, without any explicit configuration required by the developer. These libraries are typically installed as part of the JRE and are not usually managed by build tools or IDEs.

This means that all Java projects running on the same `JVM` instance will share the same set of bootstrap libraries. It is worth noting that while **the bootstrap libraries** are shared by all projects, they are managed separately from **the shared extension libraries**.
By default, `IntelliJ IDEA` uses a single global extension library directory to store shared libraries that can be used by multiple projects. This can give the impression that all projects are using the same set of libraries.  
However, `IntelliJ IDEA` has its own project-specific configuration and have their own independent libraries and dependencies.  

When running a Java program in `IntelliJ`, the `JVM` will first search for the required classes in the bootstrap libraries. If the required classes are not found in the bootstrap libraries, the `JVM` will then search in the `classpath`, By default, the project-specific libraries are added to the `classpath` before the shared extension libraries. So, the `IntelliJ IDEA` searches for libraries in the project-specific libraries first and then in the shared extension libraries.  
The order of the `classpath` in `IntelliJ IDEA` can be configured in the project settings. 
