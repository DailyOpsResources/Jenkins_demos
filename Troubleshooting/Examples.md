#Here are few examples of a failed console output in Jenkins <br>
#In most of the cases you might want to get back to developer to fix the code, pluging erros, (or) fix network/permission issues.<br>

**Example 1:** In this example, the Jenkins pipeline consists of two stages: "Setup" and "Tests." The setup script fails due to a missing module (xyz) when executing the npm install command. The failure is reported in the console output. Similarly, the test script (npm run test) in the "Tests" stage fails, causing the overall build to fail.
```
Started by user Alex Thompson
Running on Production Agent in /var/jenkins/workspace/Run Tests
[Pipeline] stage
[Pipeline] { (Setup)
[Pipeline] sh
Running setup script...
+ npm install
npm ERR! Cannot find module 'xyz'
...

[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Tests)
[Pipeline] sh
Running test script...
+ npm run test
npm ERR! Test execution failed. See above for more details.
...

[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
ERROR: Build failed with an exception.
```


**Example 2:**In this example, the pipeline's "Build" stage runs a Maven build script (mvn clean install). However, the build fails due to a compilation error. The error message indicates that the package com.example does not exist, causing the compilation failure.
```
Started by user Jessica Lee
Running on Development Agent in /var/jenkins/workspace/Build and Deploy
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
Running build script...
+ mvn clean install
...
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.8.1:compile (default-compile) on project myapp: Compilation failure: error: package com.example does not exist
...

[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
ERROR: Build failed with an exception.

```


**Example 3:**In this example, the "Build" stage runs a build script using the make command. However, the build fails with an error related to a missing file (file1.c). The console output displays the error message from the gcc compiler indicating that the file is not found, causing the build failure.
```
Started by user Ryan Wilson
Running on Development Agent in /var/jenkins/workspace/Build and Test
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
Running build script...
+ make
...
gcc: error: file1.c: No such file or directory
...

[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
ERROR: Build failed with an exception.

```


Example 4: In this example, the "Tests" stage runs integration tests using pytest with the --integration flag. However, one of the tests fails with an assertion error. The console output displays the assertion error message, indicating that the test expected a response of 'success' but received 'failure' instead.
```
Started by user Olivia Green
Running on Development Agent in /var/jenkins/workspace/Run Integration Tests
[Pipeline] stage
[Pipeline] { (Tests)
[Pipeline] sh
Running integration tests...
+ pytest --integration
...
E       AssertionError: Expected response 'success' but received 'failure'

...

[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
ERROR: Build failed with an exception.
```
