# BUILDING ELASTIC KUBERNETES SERVICE WITH TERRAFORM



## Create EKS cluster wuth Terraform
- Create a VPC using the terraform official AWS VPC module
- Create EKS cluster using the terraform official AWS VPC module

- Run ```terraform apply```

![terraform](PBL-24/terraform.png)

- Run ```aws eks update-kubeconfig --region us-east-2 --name eks-cluster --kubeconfig .kube/config```

![kubeconfig](PBL-24/kubeconfig.jpg)

## Set Context

```bash
kubectl config get-contexts

kubectl config use-context <context-name>
```

![context](PBL-24/contexts.jpg)

## Install Helm and set it up for use

```bash
sudo snap install helm --classic

helm version
```

![helm](PBL-24/helm.jpg)

## Deploy Jenkins with Helm

```bash
helm repo add jenkins https://charts.jenkins.io

helm repo update

helm install jenkins jenkins/jenkins

helm ls

kubectl get pods

kubectl describe pods jenkins-0

kubectl logs jenkins-0

kubectl exec --namespace default -it svc/jenkins -c jenkins -- /bin/cat /run/secrets/additional/chart-admin-password && echo

kubectl --namespace default port-forward svc/jenkins 8080:8080
```

![jenkins-1](PBL-24/jenkins-1.png)

![jenkins-2](PBL-24/jenkins-2.jpg)

![jenkins-3](PBL-24/jenkins-3.jpg)

![jenkins-4](PBL-24/jenkins-4.png)

## TASKS

- Install Artifactory

```bash
helm repo add jforg https://charts.jfrog.io

helm repo update

kubectl create namespace artifactory

helm install artifactory --namespace artifactory jfrog/artifactory
```

![artifactory](PBL-24/artifactory.png)


- Install Elasticsearch

```bash
helm repo add elasstic https://helm.elastic.co

helm repo update

helm install elasticsearch elastic/elasticsearch
```

![elastic](PBL-24/elastic.png)


- Install Prometheus

```bash
helm repo add prometheus-community https://prometheus-community.githu.io/helm-charts

helm repo update

helm install prometheus prometheus-community/prometheus
```

![prometheus-1](PBL-24/prometheus-1.png)

![prometheus-2](PBL-24/prometheus-2.png)


- Install Grafana

```bash
helm repo add grafana https://grafana.github.io/helm-charts

helm repo update

helm install my-release grafana/grafana
```

![grafana-1](PBL-24/grafana-1.png)

![grafana-2](PBL-24/grafana-2.png)



- Install Hashicorp Vault

```bash
helm repo add hashicorp https://helm.releases.hashicorp.com

helm repo update

helm install vault hashicorp/vault
```

![vault](PBL-24/vault.png)
