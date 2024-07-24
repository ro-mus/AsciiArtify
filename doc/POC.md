# Proof of Concept: ArgoCD Deployment on Kubernetes

## Introduction

This document provides instructions for deploying a Kubernetes cluster and setting up ArgoCD for the AsciiArtify project.

## Prerequisites

- Docker installed
- k3d installed
- kubectl installed

## Steps

### 1. Install ArgoCD

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
### 2. Check application running
```sh
kubectl get all -n argocd
```
### 3. Make port forward for accessing WEB UI
```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
### 4. Get ArgoCD Admin Password
```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```
### 5. Login to ArgoCD and create first app

Open your browser and follow link https://localhost:8080. 

Use the username `admin` and the password obtained in the previous step. Create App using Helm charts from Git repository as on example below and press Sync.

Monitor the Application Synchronization: ArgoCD monitors the specified Git repository for changes. When a change is detected (such as a new commit), ArgoCD will sync the state of the repository with the state of the Kubernetes cluster.

