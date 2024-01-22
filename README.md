kubectl create deployment nginx --image=nginx:1.10.0
kubectl get pods
kubectl expose deployment nginx --port 80 --type LoadBalancer
kubectl get services
kubectl create -f pods/monolith.yaml
  kubectl port-forward monolith 10080:80
  curl http://127.0.0.1:10080
  curl http://127.0.0.1:10080/secure
  curl -u user http://127.0.0.1:10080/login
  TOKEN=$(curl http://127.0.0.1:10080/login -u user|jq -r '.token')
  curl -H "Authorization: Bearer $TOKEN" http://127.0.0.1:10080/secure
  kubectl logs monolith
  kubectl exec monolith --stdin --tty -c monolith -- /bin/sh
    ping -c 3 google.com
cat pods/secure-monolith.yaml
  kubectl create secret generic tls-certs --from-file tls/
  kubectl create configmap nginx-proxy-conf --from-file nginx/proxy.conf
  kubectl create -f pods/secure-monolith.yaml


cat deployments/auth.yaml
kubectl create -f deployments/auth.yaml
kubectl create -f services/auth.yaml
kubectl create -f deployments/hello.yaml
kubectl create -f services/hello.yaml
kubectl create configmap nginx-frontend-conf --from-file=nginx/frontend.conf
kubectl create -f deployments/frontend.yaml
kubectl create -f services/frontend.yaml
kubectl get services frontend



