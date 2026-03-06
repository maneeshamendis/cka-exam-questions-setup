## Question : 
Create a new Ingress resource as follows:
Name: echo
Namespace : sound-repeater

#### Exposing Service echoserver-service on http://mendis.org/echo using Service port 8080
curl -o /de v/null -s -w "%{http_code}\n" http://mendis.org/echo

