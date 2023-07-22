# MLOps-model-deployment
## Project Title: Implementing Kubeflow with Kserve for Model Deployment
https://docs.google.com/document/d/1nd5hAj-uBgsyIVKBxziZz-MZJc0cC4t6bvlCmGf3_tc/edit 

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
- In mycase I use minikube

- link for implement kubeflow: https://dagshub.com/blog/how-to-install-kubeflow-locally/ 
- component after installed (do not kubectl apply all component in manifests )

```bash
kubectl get pods -A
```

```
NAMESPACE      NAME                                                     READY   STATUS     RESTARTS         AGE
auth           dex-7ff46847-dw45k                                       1/1     Running    0                71m
cert-manager   cert-manager-7fb78674d7-2pvz4                            1/1     Running    0                89m
cert-manager   cert-manager-cainjector-5dfc946d84-dkrqh                 1/1     Running    0                89m
cert-manager   cert-manager-webhook-8744b7588-kwg24                     1/1     Running    0                89m
istio-system   authservice-0                                            1/1     Running    0                80m
istio-system   istio-ingressgateway-c7fdd4bf6-b8hpn                     1/1     Running    0                89m
istio-system   istiod-6995577d4-9h9nh                                   1/1     Running    0                89m
kube-system    coredns-787d4945fb-wvgbw                                 1/1     Running    22 (110m ago)    83d
kube-system    etcd-minikube                                            1/1     Running    17 (110m ago)    83d
kube-system    kube-apiserver-minikube                                  1/1     Running    20 (110m ago)    83d
kube-system    kube-controller-manager-minikube                         1/1     Running    18 (110m ago)    83d
kube-system    kube-proxy-rdk28                                         1/1     Running    17 (110m ago)    83d
kube-system    kube-scheduler-minikube                                  1/1     Running    17 (110m ago)    83d
kube-system    storage-provisioner                                      1/1     Running    51 (9m52s ago)   83d
kubeflow       cache-server-6b44c46d47-th2s5                            0/2     Init:0/1   0                89m
kubeflow       centraldashboard-f966d7897-zrxjw                         2/2     Running    1 (36m ago)      58m
kubeflow       kubeflow-pipelines-profile-controller-6f6bc888df-2qp9s   1/1     Running    0                89m
kubeflow       metacontroller-0                                         1/1     Running    0                89m
kubeflow       metadata-envoy-deployment-7b49bdb748-p8ch2               1/1     Running    0                89m
kubeflow       metadata-grpc-deployment-6d744c66bb-pvx6r                2/2     Running    3 (88m ago)      89m
kubeflow       metadata-writer-5bfdbf79b7-5n8sc                         2/2     Running    1 (84m ago)      89m
kubeflow       minio-549846c488-5gjz8                                   2/2     Running    0                89m
kubeflow       ml-pipeline-86d69497fc-l25qz                             2/2     Running    10 (9m7s ago)    88m
kubeflow       ml-pipeline-persistenceagent-5789446f9c-6c5cl            2/2     Running    0                88m
kubeflow       ml-pipeline-scheduledworkflow-fb9fbd76b-wc6hm            2/2     Running    0                88m
kubeflow       ml-pipeline-ui-74fcbdddd9-ct7fz                          2/2     Running    15 (9m1s ago)    88m
kubeflow       ml-pipeline-viewer-crd-bdf696cb9-gxsrf                   2/2     Running    1 (88m ago)      88m
kubeflow       ml-pipeline-visualizationserver-845d745b46-76pdx         2/2     Running    13 (9m11s ago)   88m
kubeflow       mysql-5f968d4688-c8krz                                   2/2     Running    0                88m
kubeflow       profiles-deployment-7bc6469cdd-65lvr                     3/3     Running    9 (12m ago)      79m
kubeflow       tensorboards-web-app-deployment-7d4f745c6d-nzqn4         2/2     Running    0                61m
kubeflow       volumes-web-app-deployment-5f794d44cf-9945d              2/2     Running    0                67m
kubeflow       workflow-controller-56cc57796-mbzvk                      2/2     Running    12 (9m58s ago)   88m
```

#### 2. Install and configure Kserve on the same cluster
