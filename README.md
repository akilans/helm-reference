# Helm Reference

### Installation

- Kubectl with running kubernetes cluster are needed

```bash
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

echo "source <(helm completion bash)" >> ~/.bashrc
```

### Commands

```bash
helm search hub wordpress # search for wp in hub
helm repo add bitnami https://charts.bitnami.com/bitnami # add a repo
helm search repo wordpress # search for wp in all repos(bitnami here)
helm repo list # list all the repos
# amaze-surf is a release name
helm install amaze-surf bitnami/apache # install(create a release) app from repo
helm list # list all the releases
helm history amaze-surf # list all the history of releases
helm uninstall amaze-surf #uninstall app
helm repo remove bitnami # remove repo
helm upgrade dazzling-web bitnami/nginx --version 13.2.29 # upgrade the new helm chart version
helm rollback dazzling-web 3 # rollback to revision 3
```

### Create and Validate Helm Charts

```bash
helm create 01_httpd_basic_chart
helm lint ./01_httpd_basic_chart/
helm template ./01_httpd_basic_chart/
helm install httpd-1 ./01_httpd_basic_chart --dry-run
```

### Conditions ( if ) - Blocks ( with ) and Range

```bash
helm package webapp-color/
```
