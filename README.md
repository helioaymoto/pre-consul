# pre-consul
Consul service discovery in Kubernet Cluster.

## About this project
This is a preconditional Storage configuration required to install consul in a Kubernet Cluster.


## Come Observation about this project
1) Implement Storage class required to install Consul in Kubernet Cluster
2) It is necessary to have at least 3 workers nodes in a kubernet cluster
3) It is using Local Volume in to make easy the configuration, but it is possible to use any other type of Storage (NFS, iSCSI, Ceth etc)
4) Consul Cluster will have 3 servers, so this project will creat3 3 storages classes where each one will have volume in each worker node of the kubernet cluster
5) StorageClass, PV, PVC and Consull will installed in a name space called **Consul**

## Step by Step to build
```
git clone https://github.com/helioaymoto/pre-consul.git
cd pre-consul
kubectl create -f namespace.yaml
kubectl create -n consul -f storageClass.yaml
kubectl create -n consul -f persistentVolume.yaml
kubectl create -n consul -f persistentVolumeClaim.yaml

kubectl get pods -n=consul
kubectl get storageclass -n=consul
kugectl get pv -n=consul
kugectl get pvc -n=consul
```
Next you can follow the instruction in HashiCorp 
https://www.consul.io/docs/platform/k8s/run.html
