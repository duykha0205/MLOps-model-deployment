# MLOps-model-deployment
## Project Title: Implementing Kubeflow with Kserve for Model Deployment

#### Project Description: 
Kubeflow is an open-source platform that makes it easy to deploy and manage machine learning workflows on Kubernetes. Kserve is another open-source platform that provides a serverless model deployment system for Kubernetes.

In this project, you will be setting up a Kubeflow cluster and integrating it with Kserve to deploy a model trained on a dataset. You will then use this setup to track the performance of the deployed model.


#### Project Tasks:
1. Install and configure Kubeflow on a Kubernetes cluster
2. Install and configure Kserve on the same cluster
3. Write a Python script to train a model on a dataset
4. Use Kserve to deploy the trained model as a serverless deployment on Kubernetes
5. Write a Python script to test the deployed model's performance using the Kserve REST API.
6. Use Kubeflow to create an experiment and track the performance of the deployed model

## =====GUIDE LINE ==========
#### 1. Install and configure Kubeflow on a Kubernetes cluster

- Start cluster with minikube (or microk8s)
- link for install kubeflow: https://www.kubeflow.org/docs/components/pipelines/v1/installation/localcluster-deployment/

```bash
# env/platform-agnostic-pns hasn't been publically released, so you will install it from master
export PIPELINE_VERSION=2.0.0
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic-pns?ref=$PIPELINE_VERSION"
```


