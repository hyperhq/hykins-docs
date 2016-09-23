
- jenkins plugin
https://wiki.jenkins-ci.org/display/JENKINS/CloudBees+Docker+Hub+Notification

```
$ curl -vX POST -H "Content-Type: application/json" http://$JENKINS_URL:8080/dockerhub-webhook/notify -d @payload/public-repository-payload.json
```
