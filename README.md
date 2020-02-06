# GitHub jib issue #2267

See: https://github.com/GoogleContainerTools/jib/issues/2267

Steps to reproduce:

* clone repo:
  ```bash
  git clone https://github.com/daggerok/github-jib-issue-2267 
  ```
* build project for fat jar configuration using jib maven plugin version: 2.0.0 and then run docker container:
  ```bash
  ./mvnw -Djib-maven-plugin.version=2.0.0
  docker run --rm -it daggerok/github-jib-issue-2267-app-2.0.0
  # verify it doesn't work: find similar output:
  no main manifest attribute, in /tmp/classpath/app-0.0.1-SNAPSHOT.original.jar
  ```
* run same build but with version 1.8.0 this time and verify, everything is working as expected:
  ```bash
  ./mvnw -Djib-maven-plugin.version=1.8.0
  docker run --rm -it daggerok/github-jib-issue-2267-app-1.8.0
  # expected output..
  ```

[Resolution](https://github.com/GoogleContainerTools/jib/issues/2267#issuecomment-583124177): with 2.0.0 using fat jars is not possible anymore.
Check alternative [here](https://github.com/GoogleContainerTools/jib/issues/2267#issuecomment-583107466) or [here](https://github.com/GoogleContainerTools/jib/issues/2267#issuecomment-583124177).
