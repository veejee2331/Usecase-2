#   USECASE-2 (Integration GIT,Maven,Jenkins & Tomcat)

# What you will be learn this usecaseÂ :

As IT employees we work on many areas ( coding,support,infrastructure ) but while onboarding any new service we really are not aware how exactly code will deploy to production . There  are many possibilities  we can onboard our requirements to production .This use case will explain one of the ways to deploy our code to prod. 

This video  I have explained  how to troubleshoot the issues  also . After this recording was completed I had recorded another video without troubleshooting . But I feel People need to learn how to correct the mistakes also . So I preferred to upload this video . Keep Fail and learn more 

# Architecture
![Watch the image](/GITTOMCATSREE.png)

# Steps

 -  step1: Install Jenkins,Maven,GIT and Tomcat
 -  step2: Install Basic plugins  
 -  step3: Update Credentials
 -  step4: Create maven project
 -  step5: How to automate the Deployment


# step1: Install Jenkins,Maven,GIT and Tomcat

  Please watch ealier video's ( How to install Jenkins, Maven and Tomact) and follow the document attached  files in same repository
  
  Once Jenkins, maven and tomcat ready

#  step2: Install basic jenkins plugins

install ð¦ðð¯ðð§ ð¢ð§ð¯ð¨ð¤ðð« ð©ð¥ð®ð ð¢ð§ , ð¦ðð¯ðð§ ð¢ð§ð­ðð ð«ðð­ð¢ð¨ð§ , ððð©ð¥ð¨ð² ð­ð¨ ðð¨ð§ð­ðð¢ð§ðð« ð©ð¥ð®ð ð¢ð§ , ð ð¢ð­ð¡ð®ð ð¢ð§ð­ðð ð«ðð­ð¢ð¨ð§ install these plugin in manage jenkins--> plugin manager--> available --> install without restart
 
# Step3: Update credentails 

 manage jenkisn --> Credentials --> jenkins --> Global credentials --> add credentail  ( tomcat credential as you added on manager-scripton tomcatuser.xml like .. <user username="ððð©ð¥ð¨ð²ðð«" password="ððð©ð¥ð¨ð²ðð«" roles="manager-script"/> )

# Step4: Create maven project 

create new item --> select maven project--> ok --> chcek Source Code Management --> git-->  delcared 'https://github.com/veejee2331/webapplication.git' (Repository URL)--->Brach to build 'main' --> Goals and option 'clean install package ' --> Then come to Post-build Actions--> Deploy war/ear to a container --> WAR/EAR files --> **/*.war --> Add Containers -->' Tomcat 9.x Remote  ' -->select credentail what you given -->  Tomcat url ' (give tomcat url ex: http://54.152.11.147:8090/) --> Save( select credntial)

# Points need to chcek before click build

Manage Jenkins --> Golbal tool configuration --> ðð«ð ð²ð¨ð® ð®ð©ððð­ðð ððð ð¨ð« ð§ð¨ð­

Manage Jenkins --> Golbal tool configuration --> ðð«ð ð²ð¨ð® ð®ð©ððð­ðð ððð¯ðð§ ðð¨ð¦ð ðð¢ð«ððð­ð¨ð«ð²  ð¨ð« ð§ð¨ð­

Thenkn click on build

- How  you test --> http://IPADDRESS:8090/URI/ 

# step5: How to automate the Deployment

- Please update Configuration of maven job --> Build Triggers --> Poll SCM --> */2 * * * * --> save 
- While updating the git url please Fork the folder ( https://github.com/veejee2331/webapplication.git) then modify index.html

Test Again 
