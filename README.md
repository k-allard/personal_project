Sessions' replication through Spring Boot microservices using Hazelcast

Endpoints:
1. `/`
2. `/put` 
3. `/get`

_______
- ``minikube delete``
- ``minikube start``
- ``eval $(minikube docker-env)``
- ``alias mmvn='/Applications/IntelliJ\ IDEA.app/Contents/plugins/maven/lib/maven3/bin/mvn'``
- ``mmvn clean compile com.google.cloud.tools:jib-maven-plugin:1.8.0:dockerBuild`` - compiles the application, 
  creates a Docker image and registers it in the local container registry
- ``kubectl apply -f rbac.yaml`` - role-based access control (RBAC) configuration
- ``kubectl apply -f kubernetes.yaml`` - deployment configuration which builds a service with two pods. 
  Each of these pods will run one container which is built with application image    
- ``kubectl get pods``  
- ``minikube ip``  
- ``curl --cookie cookies.txt --cookie-jar cookies.txt -s -L "http://192.168.59.109:31000/put?key=myKey&value=hazelcast"``  
- ``while true; do curl --cookie cookies.txt --cookie-jar cookies.txt -s -L "http://192.168.59.109:31000/get?key=myKey"; echo; sleep 2; done``  
- ``minikube dashboard``