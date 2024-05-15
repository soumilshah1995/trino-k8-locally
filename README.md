# trino-k8-locally

# Installing Helm, kubectl, and Trino using Helm

## Prerequisites

Before proceeding, ensure you have the following prerequisites installed:

- [Homebrew](https://brew.sh/) (for macOS and Linux users)
- [Helm](https://helm.sh/docs/intro/install/) (version 3 or later)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) (Kubernetes command-line tool)

## Installation

### Helm

```bash
brew install helm
```

kubectl
```
brew install kubectl
```

Trino Helm Chart
```
helm repo add trino https://trinodb.github.io/charts

helm install example-trino-cluster trino/trino \
--set server.workers="2" \
--version 0.20.0 \
--set image.tag="400" \
--set coordinator.jvm.maxHeapSize="4G" \
--set worker.jvm.maxHeapSize="4G" \
--set service.type=LoadBalancer

```
# Jupyter notebooks 
```
!pip install trino
!pip install ipython-sql
%load_ext sql
%sql trino://admin@localhost:8080/default
%sql USE tpcds.sf100000
%%time
%sql select * from customer limit 2

```

# change Pods
```
!helm upgrade example-trino-cluster trino/trino --set server.workers=6 --set service.type=LoadBalancer
%%time
%sql select count(*) from customer
```

Feel free to add further explanations or instructions as needed!
