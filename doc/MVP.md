# MVP Deployment with ArgoCD

This document outlines the steps taken to deploy the MVP of the "AsciiArtify" project using ArgoCD.

## Setup Steps

### 1. Log in to ArgoCD

### 2. Create the ArgoCD Application

* Click "New App".
* Fill the config as in example:
    * Application Name: demo
    * Project: default
    * Sync Policy: Manual or Automated
    * Sync Options: Auto-Create namespace
    * Repository URL: https://github.com/ro-mus/go-demo-app.git
    * Revision: HEAD
    * Path: /helm
    * Cluster: https://kubernetes.default.svc
    * Namespace: demo
* Click "Create".

![Image](https://github.com/ro-mus/AsciiArtify/blob/main/img/ArgoCD-MVP-1.gif)

### 3. Sync Demo Application

* Click "Sync".
* Choose options and resources to sync.
* Click "Synchronize".

![Image](https://github.com/ro-mus/AsciiArtify/blob/main/img/ArgoCD-MVP-2.gif)

### 4. Let's try to change something to verify synchronization process

* For example change in values.yaml gateway type frome LoadBalancer to NodePort

![Image](https://github.com/ro-mus/AsciiArtify/blob/main/img/ArgoCD-MVP-3.gif) 

* Verify sync process 

![Image](https://github.com/ro-mus/AsciiArtify/blob/main/img/ArgoCD-MVP-4.gif)

### 5. Enable automated synchronization and verify

* Click "Details", next Sync Policy "Enable Auto-Sync"
* Let's revert our last commit

![Image](https://github.com/ro-mus/AsciiArtify/blob/main/img/ArgoCD-MVP-6.gif)

* Wait 180 sec (default timeout) or click "Refresh"

![Image](https://github.com/ro-mus/AsciiArtify/blob/main/img/ArgoCD-MVP-5.jpg)
