Install a plugin named AWS ELASTIC BEANSTALK
and create a beanstalk with docker platform in aws

```
New item > freestyle
```
```
source code management - git - https://github.com/arghya-roy/beanstalk1.git
```
```
1. Build Step - AWS Elastic Beanstalk
2. AWS credential and region - add - jenkins - add aws wwith access key and secret key
3. select region - ap- south-1
4. number of attems = 30
5. give application name and env name
6. root object = . ( it will make zip of all in workspace)
7. include = */
8. Version Label Format = ${BUILD_NUMBER}
9. Amount of time to sleep between deployment status checks (seconds) = 90
10. Number Of Attempts = 30
11. Ensure Health is Green after deploy? = checkrd
```
it picks all files (with dockerfile and docker-compose) from git and make them zip 
and push them in elastic beanstalk.

documentation -

```
In order to understand how this plugin works, you need to understand how AWS Elastic Beanstalk works. In a nutshell:

1. You package a zip file with the contents of your app (or the plugin creates you one)
2. This zip file is uploaded as a new S3 Object in a bucket you control
3. The CreateApplicationVersion API call is done in your application, pointing to the file created in the previous step
4. You call the UpdateEnvironment call with the versionLabel from the previous step, triggering an update

The Git Endpoints AWS Publishes automate steps 1-3 and optionally 4. Unfortunately, this is undocumented and AWS so far hasn't released its inner workings despite our attempts to call for help.

This plugin does steps 1-3 and if an environment name is specified and its active, it also does the UpdateEnvironment API call. If you enable the "Zero Deployment" Flag, it creates a parallel environment and deploys into it.We've written this in order to allow more streamlined deployments from Jenkins, specially for non-Maven builds with minimal tweaking

(for Maven builds, we advise you to look at our ingenieux Beanstalker, our Maven Plugin. You'll love it!)

Setting up your Jobs
Once installed, the plugin will allow you to add a new Build Step in Jenkins. You have two options:

a. Build a Zip / WAR file yourself. In this case, just mention "Root Object" as the path to the generated file.

The values for includes/excludes are unnecessary. As for Version Label Format, see some available variables on this url. 

b. You want us to build your zip file. The plugin allows you to do it, by specifying include/exclude globs, as long as you define a directory (which, in this case, is the Root Object). Example on a Node.js project:

Root Object: . (the base directory)
Includes: */
Excludes: */.git/,/node_modules/*
Once your build is finished, the plugin does the rest.
```
