Install a plugin named AWS ELASTIC BEANSTALK

```
New item > freestyle
```
```
source code management - git https://github.com/arghya-roy/beanstalk1.git
```
```
Build Step - AWS Elastic Beanstalk
AWS credential and region - add - jenkins - add aws wwith access key and secret key
select region - ap- south-1
number of attems = 30
give application name and env name
root object = . ( it will make zip of all in workspace)
include = */
Version Label Format = ${BUILD_NUMBER}
Amount of time to sleep between deployment status checks (seconds) = 90
Number Of Attempts = 30
Ensure Health is Green after deploy? = checkrd
```
