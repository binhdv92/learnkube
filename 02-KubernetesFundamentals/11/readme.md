kubectl port-forward service/service-hello-world 3000:80
kubectl port-forward --address 0.0.0.0 service/service-hello-world 3000:80
curl server.example.com:3000

kubectl describe pod rke2-ingress-nginx-controller-f6p2h -n kube-system | grep Ports

kubectl port-forward  --address 0.0.0.0 rke2-ingress-nginx-controller-f6p2h 3000:80 --namespace kube-system