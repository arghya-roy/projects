We know how to use work with each and Git, Jenkins independently. What if you want to collaborate these two? that is where Simple DevOps project helps you. Follow below steps if you are a new guy to DevOps. You love it. 

### Follow this article in **[YouTube](https://www.youtube.com/watch?v=Z9G5stlXoyg)**  
#### Prerequisites
1. launch a EC2 instance with tomcat installation **[installation steps video](https://youtu.be/m21nFreFw8A)
2. launch a Jenkins server **[Get Help here](https://www.youtube.com/watch?v=M32O4Yv0ANc)
3. in jenkins install maven plugin and deploy to container plugin
4. 
- setup credentials
  - `manage jenkins` > `credentials` > `jenkins` > `Global credentials` > `add credentials`
    - Username	: `username which is given at the time of tomcat installation`
    - Password : `password which is given at the time of tomcat installation`
    - id      :  `Tomcat_user`
    - Description: `Tomcat user to deploy on tomcat server`

### Part-01 : Adding steps for Integration
### Steps to create Jenkin job
1. Login to Jenkins console
1. Create *Jenkins job - maven job*, Fill the following details,
   - *Source Code Management:*
      - Repository: `https://github.com/ValaxyTech/hello-world.git`
      - Branches to build : `*/master`  
   - *Build:*
     - Root POM:`pom.xml`
     - Goals and options : `clean install package`

### Part-02: Adding Deployment Steps 

 - Post build Steps
   - Deploy war/ear to container
      - WAR/EAR files : `**/*.war`
      - Containers : `Tomcat 8.x`
         - Credentials: `Tomcat_user` (which created in above step)
         - Tomcat URL : `http://<PUBLIC_IP>:<PORT_NO>`

Save and run the job now.

### Port-03 : Continuous Integration & Continuous Deployment (CI/CD)
Now job is running fine but to make this as Continuous Integration and Continuous Deployment Tod do that go back and modify job as below. 
  - Build Triggers
    - Poll SCM
      - schedule `*/2 * * * *`

Save the job and modify the code in GitHub. Then you could see your job get trigger a build without any manual intervention.


