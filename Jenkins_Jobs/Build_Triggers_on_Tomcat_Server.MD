# Modify the project "Deploy_on_Tomcat_Server"
1. Go to Build triggers session
2. Build periodically will build at a specific time (Crontab)
3. Poll SCM (This option will trigger build when there is change in the code, It will constantly check your repo.)
4. After you save it will automatically build for the first time and then at each change

Your can Update your hello-world code to test, located here https://github.com/itresolve/hello-world/blob/master/webapp/src/main/webapp/index.jsp

So far we have automate our code to execute when there is a change, we have setup CI/CD (delivery) with Jenkins as build and deployment tool.
