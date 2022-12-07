# Kubernetes Cheat Sheet

1. [Basic Commands](#basic-commands)
   - [List all pods](#list-all-pods)
   - [List all deployments](#list-all-deployments)
   - [Create a deployment](#create-a-deployment)
   - [Scale a deployment](#scale-a-deployment)
   - [Update a deployment](#update-a-deployment)
   - [Delete a deployment](#delete-a-deployment)
2. [Namespaces](#namespaces)
   - [List all namespaces](#list-all-namespaces)
   - [Create a namespace](#create-a-namespace)
   - [Set the current namespace](#set-the-current-namespace)
   - [Delete a namespace](#delete-a-namespace)
3. [Services](#services)
   - [List all services](#list-all-services)
   - [Create a service](#create-a-service)
   - [Delete a service](#delete-a-service)
4. [Other Commands](#other-commands)
   - [Get the version of Kubernetes installed](#get-the-version-of-kubernetes-installed)
   - [Get help with a Kubernetes command](#get-help-with-a-kubernetes-command)

## Basic Commands

#### List all pods:
```Bash
kubectl get pods
```

#### List all deployments:
```Bash
kubectl get deployments
```

#### Create a deployment:
```Bash
kubectl create deployment [deployment_name] --image=[image]
```

#### Scale a deployment:
```Bash
kubectl scale deployment [deployment_name] --replicas=[number_of_replicas]
```

#### Update a deployment:
```Bash
kubectl set image deployment [deployment_name] [container_name]=[new_image]
```

#### Delete a deployment:
```Bash
kubectl delete deployment [deployment_name]
```

## Namespaces

#### List all namespaces:
```Bash
kubectl get namespaces
```

#### Create a namespace:
```Bash
kubectl create namespace [namespace_name]
```

#### Set the current namespace:
```Bash
kubectl config set-context --current --namespace=[namespace_name]
```

#### Delete a namespace:
```Bash
kubectl delete namespace [namespace_name]
```

## Services

#### List all services:
```Bash
kubectl get services
```

#### Create a service:
```Bash
kubectl expose deployment [deployment_name] --name=[service_name] --type=LoadBalancer --port=[external_port] --target-port=[internal_port]
```

#### Delete a service:
```Bash
kubectl delete service [service_name]
```

## Other Commands

#### Get the version of Kubernetes installed:
```Bash
kubectl version
```

#### Get help with a Kubernetes command:
```Bash
kubectl [command] --help
```
