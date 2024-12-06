# Kubernetes Application with MongoDB and Mongo-Express on Minikube  

This project demonstrates deploying a Kubernetes application on Minikube. The setup includes a **MongoDB** instance for database operations and **Mongo-Express** for interacting with the database via a web-based GUI.  

---

## 🚀 Features  

- **MongoDB Deployment**: Deploy a database using Kubernetes manifests.  
- **Mongo-Express Deployment**: User-friendly interface for managing MongoDB.  
- **Service Management**: Exposes MongoDB and Mongo-Express services in the cluster.  
- **Local Kubernetes Cluster**: Use Minikube for local Kubernetes environment.  

---

![Image of the project archtecture](https://miro.medium.com/v2/resize:fit:720/format:webp/1*3LPpltA8QAbLCcwBsVj8sQ.png)

## 📋 Prerequisites  

Before starting, ensure you have the following installed:  

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)  
- [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)  
- [Docker](https://www.docker.com/)  

---

## ⚙️ Setting Up the Project  

### Start Minikube  
```bash  
minikube start  
```  

---

## 🛠 Deploying MongoDB and Mongo-Express

### Step 1: Deploy Secret Service  

Use the following YAML file [`1_mongoDB-secret.yaml`](./1_mongoDB-secret.yaml):
```bash  
kubectl apply -f 1_mongoDB-secret.yaml  
``` 

### Step 2: Deploy MongoDB and Internal Service

Use the following YAML file [`2_mongoDB-config.yaml`](./2_mongoDB-config.yaml):
```bash  
kubectl apply -f 2_mongoDB-config.yaml  
``` 

### Step 3: Configuration and Deployment of Configmap  

Use the following YAML file [`3_mongo-configmap.yaml`](./3_mongo-configmap.yaml)  
```bash  
kubectl apply -f 3_mongo-configmap.yaml  
```

### Step 4: Configuration and Deployment of Mongo-express  

Use the following YAML file [`4_mongo-express.yaml`](./4_mongo-express.yaml)  
```bash  
kubectl apply -f 4_mongo-express.yaml  
```  

---

## 🌐 Accessing Mongo-Express  

After deployment, you can access Mongo-Express through Minikube:

```bash  
minikube service mongo-express-service  
```  

This command will open Mongo-Express in your default web browser.  

---

## 📊 Monitoring the Application  

Check the status of your deployments and services:  

```bash  
kubectl get all
```
View logs of MongoDB and Mongo-Express:

```bash  
kubectl logs deployment/mongo
kubectl logs deployment/mongo-express   
```  

---

## 🧹 Cleaning Up  

To delete all resources:  
```bash  
kubectl delete namespace mongo-app  
```  

--- 

## 📖 References
1) [Kubernete Crash Course Youtube With Nana](https://www.youtube.com/watch?v=X48VuDVv0do)
2) [Deploying MongoDB and Mongo-Express on Kubernetes using Minikube](https://medium.com/@m.ibtisam.syed/deploying-mongodb-and-mongo-express-on-kubernetes-using-minikube-including-secret-configmap-6cc994933ff2)

## 📖 Additional Resources  

- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)  
- [MongoDB Kubernetes Guide](https://www.mongodb.com/kubernetes)  
- [Mongo-Express on Docker Hub](https://hub.docker.com/_/mongo-express)  
