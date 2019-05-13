# public_rep
Public Repository

This is a public repository.

I have a git-webhook created in GIT, so any commits here to the master will trigger the corresponding job in Jenkins 
that has the following setting:

JENKINS CONFIGURATION :
Build Trigger:

"GitHub hook trigger for GITSCM polling" - Checked

GIT CONFIGURATION
Create a webhook.
Payload : http://localhost:8080/github-webhook/
In GIT, Go to settings >> webhooks ; Click "Add Webhooks" 
Payload URL : This is the Jenkins Server public URL over the internet. Since Jenkins runs in a private IP within my Home network, GIT that is on Cloud will not be able to identify my "http://localhost:8080/. So we nned to ensure Jenkins is available to GIT on a public URL, else we utilize a utility called ngrok.exe that opens a http tunnel to port 8080 on which our Jenkins is running. ( in CMD propmt, go to the directory of ngrok and type ngrok http 8080 . It will give you two public URL ( http & https ). e.g. http://72d81f6c.ngrok.io Copy this as the Payload URL in GIT webhook and end it with /github-webhook/. The / at the end should not be forgotten. http://72d81f6c.ngrok.io/github-webhook/ 
