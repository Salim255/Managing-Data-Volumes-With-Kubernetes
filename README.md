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
