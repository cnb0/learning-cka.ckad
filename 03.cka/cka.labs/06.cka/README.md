# CKA Learning Repo

Notes and preparation materials for Certified Kubernetes Administrator Exam. This repo may also contain additional resources and links which are not related to CKA, but generally useful for Kubernetes administration


# Folder structure

* README.md - outline, plan, structure etc.
* notes/ - Notes I prepared while learning, based on curriculm. They are organized on the order of curriculm and have a number prefix. There are some additional notes I added randomly, they won't have this number prefix
* tests/ - Practice tests I went through and their solution. In the order of curriculm
* yamls/ - Yaml files, certs etc. I created as part of the practice tests
* lxc.md - instructions to setup lxc containers
* kubernetes-hard-way-\*.md - Instructions I followed to setup kubernetes based on the famous `kubernetes the hard way` guide

# Things to learn and research

* LXC containers
* Kubernetes the hard way <https://github.com/kelseyhightower/kubernetes-the-hard-way>
* [killer.sh] Possibly a good way to experience the exam environment. Need to check if it provides free access
* <https://github.com/alijahnas/CKA-practice-exercises>
* [https://medium.com/@pmvk/tips-to-crack-certified-kubernetes-administrator-cka-exam-c949c7a9bea1]
* play with kind
* RBAC and certificates and stuff
* PriorityClass, ResourceQuotas, NetworkPolicy
* Generators for yaml
* jq and yq
* Explore jsonpath
* Learn kustomize
* awk, grep regex, xargs etc



# Resources

The majority of tasks in the CKA will also be around creating Kubernetes resources, like its tested in the CKAD. So we suggest to do:
Maybe 2–3 times https://github.com/dgkanatsios/CKAD-exercises
Know advanced scheduling: https://kubernetes.io/docs/concepts/scheduling/kube-scheduler

Components

The other part is understanding Kubernetes components and being able to fix and investigate clusters. Understand this: https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster
When you have to fix a component (like kubelet) in one cluster, just check how its setup on another node in the same or even another cluster. You can copy config files over etc
If you like you can look at Kubernetes The Hard Way once. But it's NOT necessary to do, the CKA is not that complex. But KTHW helps understanding the concepts
You should install your own cluster using kubeadm (one master, one worker) in a VM or using a cloud provider and investigate the components
Know how to use kubeadm to for example add nodes to a cluster
Know how to create an Ingress resources
Know how to snapshot/restore ETCD from another machine

# Plan

- [x] Complete `Kubernetes the hard way` using LXC containers and document the steps (Or maybe using digitalocean droplets) - try multiple times
- [x] Go through handbook and curriculm
- [x] Register for the Exam
- [x] Learn RBAC from official doc
- [x] Learn each topic from curriculm separately and prepare notes
- [x] Install using kubeadm on digitalocean droplets and play with it
- [x] Go through a CKA excercises repo and try out all the excercises
- [x] Master the kubernetes official documentation
- [x] Take some sample test from somewhere
- [ ] Install kubernetes in a single node using binaries, without tls and all
- [ ] Try out a full sample test locally
- [ ] Try out all my excercises again
- [x] Try out killer.sh free sessions
- [x] Schedule the exam (sometime around august last week or September first week 2021)
- [x] Go through notes again
- [x] Take the exam!


# Links

* kubernetes-the-hard-way steps using LXC containers 

# Environment

## Kind cluster

Kubernetes in docker is the easiest way to get started with kubernetes. It has most of the things needed to practice in-cluster scenarios.
Also, it is 1.21 Kubernetes, which is what we'll be having in the exam this quarter. It uses etcd too. So  we can try out etcd commands as well - like backup and restore


```
kind create cluster
❯ kind create cluster
Creating cluster "kind" ...
 ✓ Ensuring node image (kindest/node:v1.21.1) 🖼
 ✓ Preparing nodes 📦  
 ✓ Writing configuration 📜 
 ✓ Starting control-plane 🕹️ 
 ✓ Installing CNI 🔌 
 ✓ Installing StorageClass 💾 
Set kubectl context to "kind-kind"
You can now use your cluster with:

kubectl cluster-info --context kind-kind
```

## Setting context and namespace

```
k config set-context kind-kind --namespace=kube-system
k config use-context kind-kind
```

## Learning Plan

Module 1 - Cluster Architecture, Installation & Configuration - 25%
* Day - 1 : Kubernetes the hard way
* Day - 2 : Kubernetes the hard way
* Day - 3 : RBAC basics
* Day - 4 : RBAC yamls and excercises - role, clusterole, serviceaccount, clusterrolebinding, rolebinding
* Day - 5 : certificates, creating new user, kubeadm
* Day - 6 : Setup cluster using kubeadm, complete kubeadm notes
* Day - 7 : Setup HA multi master cluster (stacked) using kubeadm
* Day - 8 : kubeadm cluster setup and kubeadm join on DO droplets. etcd backup and restore
* Day - 9 : kubeadm version upgrade, remove worker nodes

Module 2 - Workloads and Scheduling - 15%
* Day - 10  : Deployments, Rolling updates, rollback, scale
* Day - 11  : Off
* Day - 12  : configmap, secrets - CRUD, mounting, injecting into pods
* Day - 13  : Scaling application, HPA
* Day - 14  : PDB, Lifecycle hooks, Container probes, Resource limits, LimitRange, Quota, PriorityClass, Manifest and templating tools

Module 3 - Services and Networking - 20%
* Day - 15  : Concepts - cluster architecture and components
* Day - 16  : Concepts - Containers, workloads
* Day - 17  : Concepts - services, load balancing and networking, storage
* Day - 18  : Off
* Day - 19  : Networking model, services, ingress, create excercises for networking
* Day - 20  : CoreDNS, CNI, hands on excercises

Module 4 - Storage - 10%
* Day - 21  : Storageclass, PV, PV mode, access mode, reclaim policy
* Day - 22  : PVC, configuring apps, excercises

Module 5 - Troubleshooting - 30%
* Day - 23  : Cluster and node logging, container stdout and stderr, Monitor applications, app failure, cluster component failure
* Day - 24  : Networking troubleshooting, excercises
* Day - 25  : Killer.sh one session

Exam day : 01 September 2021

* Later - kubernetes-hard-way (for the second time), kustomize, downwardAPI, Security
* Later - Go through tasks in docs, jsonpath in depth, jq & yq?

## On exam day

on tmux, run 

```
ctrl+b
:set -g mouse on
```

use shift select to copy from tmux

set bashrc

```
alias k=kubectl
export do="--dry-run=client -o yaml"
```

vim config in `.vimrc`

```
set expandtab
set shiftwidth=2
set tabstop=2
```
