# Managing-Data-Volumes-With-Kubernetes

# State in kubernetes

## State is data created and used by your application which must not be lost

# Type of states

## 1\ User-generated data, user accounts,.. and these data often stored in a databases , but could also be files

## 2\ Intermediate results derived by the app which will be lost once the application deleted, often stored in memory, or temorary database tables or files

# So in order to do not lose data when container stoped or deleted, we must use volume to persist data, so kubernetes needs to be configured to add volumes to our containers

# 🌈 Kubernetes & Volumes

## 1\create deployment.yaml

## 2\ create service.yaml

## 3\ docker build -t crawan/kube-data-volume .

## 4\ docker push crawan/kube-data-volume

## 5\ Choose Kubernetes volumes type, we start with "emptyDir type"

# Volumes depend on the pods, because are attached to pods, so we have to deine a volume in the place where we define a pod, here will be in deplyment.yaml file

# The hostPath is better than emptyDir stype, but hostPath is node spec, so if we have multiples nodes we still have a problem with the volume, so we need an other solution because the replicas runs in differnt node will not have access to voulume that in other node, but this methode is still very useful if you want to make your data independant from diffrent pod

# ☂️ CSI ype "Container Storage interface"

## Bas side of CSI

### 1\ Valumes are detroyed when a pod is removed

### 2\ New cread pod will not have access to the data created be the old pod

# Persistent Volumes build for pod and nodes independence, how data is stored and how the are not lost when pod is distroyed or created, finding them in central plces then use the volumes in differnts pod, without editing multiple pod yaml files

# First, create the persistentVolume: run: kubectl apply -f=host-pv.yaml

# Second apply the claim to create the calim: run: kubectl apply -f=host-pvc.yaml

# Therd apply the deployment: run: kubectl apply -f=deployment.yaml

# run kubectl get pv, to get a list of all persistent volumes

# Run: $ kubectl get pvc, to your claim

# Now our pods in created by deplpyment use pvc as volume
