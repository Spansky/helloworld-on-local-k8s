# Webserver Deployment for a locally run Kubernetes

## Purpose

So you've setup a Raspberry Pi kubernetes cluster just as I did? Now you want to deploy
the first applications on it but you are unsure how to start?

This repo is for <s>you</s> me.

## Step by Step

### First website

In this repo you can find a index.html directly in the root folder. Deploy it 
as a website to your Kubernetes (K8S) Cluster with the following commands.

```bash
kubectl create namespace helloworld
kubectl create configmap hello-world --from-file ./index.html --namespace helloworld
kubectl apply -f ./hello-world.yml --namespace helloworld
```

You will be able to reach that example page by either going on 
- http://8ls.co
- http://pi501.local
- http://pi501.fritz.box





