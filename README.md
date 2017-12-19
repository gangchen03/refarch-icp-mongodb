# Deploy Highly Available MongoDB on IBM Cloud Private platform

Recently, we were asked several times on how to deploy database systems like MongoDB on IBM Cloud Private (ICP) Kubernetes platform, and ensure the deployment is highly available and scalable. The research directed us to use a Kubernetes community stable Helm chart  [mongodb-replicaset](https://github.com/kubernetes/charts/tree/master/stable/mongodb-replicaset). This chart uses the StatefulSet to enable the MongoDB replica set for high availability. The persistence is built on top of the Kubernetes PersistenceVolume. And the database is exposed as a Kubernetes Headless service. It works great if the database will only be used by application deployed in the same Kubernetes cluster, but it poses a challenge if you try to expose the MongoDB as external service or even build an in-house DaaS solution.

The first challenge is how to expose the MongoDB replica set as Services, it can't be just simply exposed as Kubernetes LoadBalancer or NodePort based service, because the MongoDB internally uses the k8s DNS name to handle the primary/slave election. You also don't want to impact how the client interacts with the MongoDB replica set. After some research and experients, we have a solution using Mongos, shards together with replica Set to solve the problem. Here is how.  

## Architecture

![Architecture](architecture_1.2.jpeg)

## Deployment Guide

Follow the instruction below to setup the instance:



## Test the deployment

## Other consideration
