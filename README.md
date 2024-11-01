# GitOps Repository for Kubernetes Infrastructure

This repository contains all the apps for my k8s infrastructure using GitOps with ArgoCD.

## Prerequisites

- **Kubernetes Cluster**: Ensure you have a running Kubernetes cluster with sufficient permissions.
- **ArgoCD**: This repository assumes that ArgoCD is installed and configured in the cluster.

## Installation Guide

To set up the entire infrastructure defined in this repository, execute the following command:

```bash
    kubectl apply -f https://raw.githubusercontent.com/rabarbra/k8s-argo-infra/refs/heads/main/root-app.yml
```

This command will deploy the main ArgoCD application, which acts as the entry point for synchronizing and managing other applications and resources in the cluster.

## Structure of the Repository

- **root-app.yml**: The main ArgoCD application that acts as a parent to other applications.
- **apps/**: Contains individual application definitions managed by ArgoCD.
- **appsets/**: Application set that creates an application for each folder in apps directory except apps/disabled.

## How GitOps Works

This repository is designed to leverage GitOps principles, where:

- **Declarative Configuration**: The entire state of the cluster is described in a versioned Git repository.
- **ArgoCD Synchronization**: ArgoCD monitors this repository and automatically applies changes to the cluster when updates are detected.

## Updating and Managing Deployments

All changes to the infrastructure should be made by updating the files in this repository and pushing to the main branch. ArgoCD will detect the changes and apply them to the cluster automatically.
