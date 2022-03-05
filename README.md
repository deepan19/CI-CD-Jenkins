# CI-CD-Jenkins
A CI/CD pipeline on Jenkins to automate parts of the SDLC of a simple maven project
[![pipeline.png](https://i.postimg.cc/5tyYkPBc/pipeline.png)](https://postimg.cc/3yMxkFf9)

Why CI/CD?
[![1-e-HRh-Jcg-QPUws99x-EDh6w.png](https://i.postimg.cc/1RBgshvx/1-e-HRh-Jcg-QPUws99x-EDh6w.png)](https://postimg.cc/kDVMvZrw)
The above is the dev-ops life cycle. The build-test-release-deploy parts of the cycle are automated using this CI/CD pipeline. Any commits made in GitHub is quickly built, unit tested, integration tested, static code analyzed and deployed if all the above pass succesfully. This is useful to avoid merge hell and quickly deploy reliable code to stakeholders to uphold agile iterations. Complex CI/CD pipelines are used in the industry to make sure only high quality code passes through and that all deployed code is tested properly.





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
Unit testing & integration testing
These nodes are essential before trying to deploy to the nexus repo. In an industry setting, we want to avoid technical debt. This is basically a small bug that when left unfixed, may grow to become a larger issue later on in the life cycle due to other integration. Thus, any code should be unit tested before deployment. 

4.
Static code analysis using SonarQube Scanner
[![sonar1.png](https://i.postimg.cc/fWdS3zY1/sonar1.png)](https://postimg.cc/K4Z8wyq5)
The above is the dashboard lauched on the sonarqube ec2 instance. This provides a brief overview of code quality, bugs and static checks. 

[![sonar2.png](https://i.postimg.cc/pdK3hnXp/sonar2.png)](https://postimg.cc/Z9KwXnNS)
THe above is a more comprehensive view. Developers will be able to easily view bugs and other errors quickly. Moreover, the ocmpany can set the standard of deployed code. This is done by configuring quality gates. These quality gates will only allow deployment to happen if certain standards are met

[![qualitygate1.png](https://i.postimg.cc/ydQjkV9D/qualitygate1.png)](https://postimg.cc/5YzLrWsJ)

5.
Deployment to Nexus Repo
[![nexus1.png](https://i.postimg.cc/T1xbdFNK/nexus1.png)](https://postimg.cc/tZrJDSjb)

This is the release repository where succesful builds in the pipeline end up in. This instance is hosted on a seperate ec2 machine from the jenkins ec2. 

