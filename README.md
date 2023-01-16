Date:  16/01/2023  Time:  00:01
Status: #idea
Tags: [[Devops]]
Repository: 

# hello-world-multibranch-jenkins
In this repo are some basic Jenkins concepts and a step by step process of building a simple jenkins multibranch pipeline.

## Plugins
these are one of the most used plugins when building a jenkins pipeline and mostly even necessary:
* pipelines
* pipeline: stage step
* For github integrations: git, github integration plugin, git client

## Credentials
### Scopes
1. Systems
   available only on jenkins server, *not* accesible by jenkins jobs
2. Global
   accesible everywhere from jenkins
3. Project
   *only* for the multibranch pipeline limited to the project
### Types
* username & password
* certificate
* secret file
* depending on plugins you might get new credential types

## Pipelines

1. freestyle
   for simple tasks / testing
2. Pipeline
   single branch for a hole delivery lifecycle builld, package, deploy etc...
3. multibranch pipeline
   for multibranch deployments

## Jenkinsfile
it can be writen as scripted pipeline or declarative pipeline
### Scripted
* first syntax
* groovy engine
* advanced scripting capabilities
### Declarative
* last adition
* easier to get started but not that powerfull
* pre-define structure
#### Structure
##### Pipeline
must be at the top level
##### agent
where to execute the pipeline
##### stages 
where the "work" happens
##### steps
all of the code that jenkins will run


```json
pipeline{
	agent any
	stages{
		stage("build"){
			steps{
				echo "building application ..."
			}
		}
		stage("test"){
			steps{
				echo "testing application ..."
			}
		}
		stage("deploy"){
			steps{
				echo "deploying application ..."
			}
		}
	}
}
```

## Triggers
### push notification
source code management system notifies jenkins on new commit
which off course is more efficient
### polling
jenkins polls the repository in regular time intervals

## Finally creating a multibranch pipeline
1. Before even starting please make sure you have jenkins installed locally or on an EC2: [[Jenkins Setup]]
2. create credentials for the github repo by going to `/manage/credentials/store/system/domain/`
3. go to create a new task and select multibranch ![[Pasted image 20230116000615.png]]
4. Select git and copy the url https://github.com/juanAmayaRamirez/hello-world-multibranch-jenkins
5. Go to pipeline credentials and create a new one with email/password of the github repository
6. After the credential is created add the credentials to pipeline
7. Create the Jenkinsfile in the root directiry of the repository 
8. Scan pipeline
9. inside the stage clik on `build now`

---
# References
* https://www.youtube.com/watch?v=pMO26j2OUME&list=PLy7NrYWoggjw_LIiDK1LXdNN82uYuuuiC