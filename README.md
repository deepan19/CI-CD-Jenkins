# CI-CD-Jenkins
A CI/CD pipeline on Jenkins to automate parts of the SDLC of a simple maven project
[![pipeline.png](https://i.postimg.cc/5tyYkPBc/pipeline.png)](https://postimg.cc/3yMxkFf9)

Why CI/CD?
[![1-e-HRh-Jcg-QPUws99x-EDh6w.png](https://i.postimg.cc/1RBgshvx/1-e-HRh-Jcg-QPUws99x-EDh6w.png)](https://postimg.cc/kDVMvZrw)
THe above is the SDLC.



Features and Concepts:

1.
AWS ec2 instances for the jenkins, sonarqube and nexus deployment:
[![awsec2.png](https://i.postimg.cc/QN4MvNnP/awsec2.png)](https://postimg.cc/c63ZnWWM)
The CI/CD pipeline will start on the jenkins ec2 instance that contains apache maven and jdk to build a simple java project.
The sonarqube instance will handle the static code analysis and the nexus instance can be thought of as the deployment server which contains releases.

2.
The pipeline's first stage is the build stage
In the build stage, we pull the code from the SCM (in this case GitHub)
[![scm.png](https://i.postimg.cc/Y9tVHWSw/scm.png)](https://postimg.cc/yJrnhW9f)

The next step in the build stage is to build the java project using maven and compile it into a artefact file

3.


