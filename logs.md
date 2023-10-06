# Monitor your Kubernetes Deployment <br/> 

## Get list of all resources

```
kubectl get all
```

<img width="981" alt="image" src="https://github.com/RSWAIN1486/k8s-local/assets/48782471/48103dbc-9864-449d-ae8c-348408c45a47"> <br/> <br/> <br/> <br/>


## Check Status of Deployment

```
kubectl describe deployment clip-deployment
```
<img width="1067" alt="image" src="https://github.com/RSWAIN1486/k8s-local/assets/48782471/11607241-7913-4cf1-81bd-5cef4dc1fd0c"> <br/> <br/> <br/> <br/>


## Describe your pod using pod-name from list all resources

```
kubectl describe <pod_name>
```
### Pod 1
![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/194516e5-6d2b-46c2-85d6-dfda41493d72) <br/> <br/> 

### Pod 2
![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/e5a7245a-c7b3-42e8-bb7f-85f2da25b6a1) <br/> <br/> <br/> <br/>


## Get the top pod and sort by cpu/memory

```
kubectl top pod --sort-by=memory
```

![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/e4916ae5-56b3-4a4e-86ff-4ba8aacea44a) <br/> <br/> <br/> <br/>


## Get the top node 

```
kubectl top node and sort by cpu/memory
```

![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/5853f6bc-8581-43fc-bd4e-6e84f05b4080) <br/> <br/> <br/> <br/>

## Get detailed yaml describing the deployment

```
kubectl get all -A -o yaml
```

![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/5d872ad9-08c5-464d-835a-be2b9acde2d0) <br/> <br/> <br/> <br/>





