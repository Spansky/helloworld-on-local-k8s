# Step by Step

```bash
kubectl create namespace helloworld
kubectl create configmap hello-world --from-file ./index.html --namespace helloworld
kubectl apply -f ./hello-world.yml --namespace helloworld
```
