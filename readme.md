# Helm for devs

## Example 1 - Walkthrough

``` powershell
kubectl get all,secret,pvc,pv,configmap
# Add the repo
helm repo add codecentric https://codecentric.github.io/helm-charts
# install the chart
helm install keycloak codecentric/keycloak
# verify the installation
kubectl get all,secret,pvc,pv,configmap
# list the releases
helm list
# modify the number of replicas
helm upgrade keycloak set replicas=3
# show the history 
helm history keycloak
# rollback to the previous version
helm rollback
# uninstall the chart
helm uninstall keycloak
# verify the uninstallation
kubectl get all,secret,pvc,pv,configmap
# show the chart
helm show chart codecentric/keycloak
# show the chart values
helm show values codecentric/keycloak

```


## Example 2 - modify values using a file

``` powershell
# create a file with the values
helm show values codecentric/keycloak > values.yaml
# modify the values
helm install keycloak -f .\testvalues.yaml  codecentric/keycloak
# verify the installation
kubectl get all,secret,pvc,pv,configmap
# uninstall the chart
helm uninstall keycloak
```


## Example 3 - What is a chart?

``` powershell
# download the chart and unzip
helm pull codecentric/keycloak –-untar
# execute the template
helm template codecentric/keycloak > templates.yaml
```

## Example 4 - Create a chart

``` powershell
# create a new chart
Helm create mychart
# install the chart
helm install mychart mychart
# verify the installation
kubectl get all,secret,pvc,pv,configmap
# uninstall the chart
helm uninstall mychart
# verify the template
helm template . > output.yaml
```