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

### Using your own Images

In the example before I used the nginx docker image. If deploying own apps
it makes sense to build docker images yourself. 

When using those docker images in Kubernetes you need to configure that you 
can login to dockerhub or whatever service you use.

Therefore I suggest you login using your docker client. Then you do the following

```bash
kubectl create secret docker-registry mysecretname \
--docker-server=https://ghcr.io \
--docker-username=xxx \
--docker-password=xxx \
--docker-email=xxx \
--namespace helloworld
```

or

```bash
kubectl create secret docker-registry mysecretname \
--from-file=.dockerconfigjson=path/to/.docker/config.json
```

When the kubernetes cluster is downloading your special docker images you might 
run into issues when you are building the images for a platform e.g. x86 but 
your cluster (in my case three arm64 Raspberry Pi 5) you have a different 
platform you will run into issues. 

What needs to be done is that you build for the right platform. 

I find it the most easy approach to do so with github actions.



