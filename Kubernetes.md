# Kubernetes Cheat Sheet

1. [Resource Management](#resource-management)
   - [Getting Resources)](#get-resources)
   - [Applying Deployments](#applying-deployments)
   - [Deleting Resources](#deleting-resources)
2. [Context](#context)
   - [Get All Contexts](#get-all-contexts)
   - [See Current Context](#see-current-context)
   - [Switch Context](#switch-context)
3. [Other Commands](#other-commands)
   - [List API Resources](#list-api-resources)
   - [Get Current Version](#get-the-version-of-kubernetes-installed)
   - [Explain](#get-documentation-for-kubernetes-resource)
   - [Help](#get-help-with-a-kubernetes-command)


## Resource management

#### Get resources
```Bash
kubectl get <resource-type>
```

```Bash
kubectl get <resource-type> <resource-name>
```

```Bash
kubectl describe <resource-type> <resource-name>
```

#### Applying deployments
```Bash
kubectl apply -f <filepath>
```

#### Deleting resources
```Bash
kubectl delete <resource-type> <resource-name>
```

## Context

#### Get all contexts
```Bash
kubectl config get-contexts
```

#### See current context
```Bash
kubectl config current-context
```

#### Switch context
```Bash
kubectl config use-context
```

## Other Commands

#### List API resources
```Bash
kubectl api-resources
```

#### Get the version of Kubernetes installed:
```Bash
kubectl version
```

#### Get documentation for kubernetes resource
```Bash
kubectl explain <resource-type>
```

```Bash
kubectl explain <resource-type>.<nested-property>
```

#### Get help with a Kubernetes command:
```Bash
kubectl [command] --help
```
