JENKINS JOB : 04_GIT_Webhook
==============================================

I have a git-webhook created in GIT, so any commits here to the master will trigger the corresponding jobs in Jenkins that have this webhook

==============================================
JENKINS CONFIGURATION :
Build Trigger: "GitHub hook trigger for GITSCM polling" - Checked

GIT CONFIGURATION :
1. In GIT, Go to settings >> webhooks ; Click "Add Webhooks" 

Payload : http://localhost:8080/github-webhook/

Payload URL : This is the Jenkins Server public URL over the internet. Since Jenkins runs in a private IP within my Home network, GIT that is on Cloud will not be able to identify my "http://localhost:8080/. So we need to ensure Jenkins is available to GIT on a public URL, else we utilize a utility called ngrok.exe that opens a http tunnel to port 8080 on which our Jenkins is running. ( in CMD propmt, go to the directory of ngrok and type ngrok http 8080 . It will give you two public URL ( http & https ). e.g. http://72d81f6c.ngrok.io Copy this as the Payload URL in GIT webhook and end it with /github-webhook/. 

The / at the end should not be forgotten. http://72d81f6c.ngrok.io/github-webhook/ 

==============================================
