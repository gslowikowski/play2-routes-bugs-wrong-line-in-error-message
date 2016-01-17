# play2-routes-bugs-wrong-line-in-error-message

Test projects (for Play! Framework versions: 2.1.x, 2.2.x, 2.3.x and 2.4.x) showing wrong error message
when compiling `conf/routes` file containing bugs. Error message shows the line after the buggy one.

Test projects are based on Play! Framework `helloworld` Scala sample.

`conf/routes` file containing bug:

```
# Routes
# This file defines all application routes (Higher priority routes first)
# ~~~~

# Home page
GET     /                           controllers.Application
# This is a comment after the line with a bug (no controller method)

# Hello action
GET     /hello                      controllers.Application.sayHello

# Map static resources from the /public folder to the /assets URL path
GET     /assets/*file               controllers.Assets.at(path="/public", file)
```

`sbt compile` command error message:

```
[info] Loading project definition from {project.path}\play24\project
[info] Set current project to helloworld (in build file:/{project.path}/play24/)
[error] {project.path}\play24\conf\routes:6: Compilation error[Controller method call expected]
[error] # This is a comment after the line with a bug (no controller method)

[error]                                                            ^
[error] (compile:playRoutes) @6ongeh9a0: Compilation error in {project.path}\play24\conf\routes:6
[error] Total time: 0 s, completed 2016-01-17 11:48:19
```
