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
