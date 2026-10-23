


newgrp docker

docker build . -f Dockerfile -t server.example.com:5000/first-k8s-app:v3

docker push server.example.com:5000/first-k8s-app:v3

kubectl apply -f namespace.yaml
kubectl apply -f values.yaml -n first-k8s-app-v3
kubectl get all -n first-k8s-app-v3

curl --header 'Host: k8s-is-great.com' http://server.example.com/v3