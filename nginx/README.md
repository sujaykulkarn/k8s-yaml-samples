NGINX-Controller installation

namespace creation - kubectl create ns ingress-space

ConfigMap creation - kubectl create configmap nginx-configuration -n ingress-space

ServiceAccount creation - kubectl create serviceaccount ingress-serviceaccount -n ingress-space

Role creation - kubectl create role -n ingress-space -f ingress-role.yml

Role Binding creation - kubectl create rolebinding -n ingress-space -f ingress-role-binding.yml

Deploy-ingress controller - kubectl create -f ingress-controller.yml

Create service to make ingress available to external users - 

Short way to get service - kubectl expose -n ingress-space deployment ingress-controller --type=NodePort --port=80 --name=ingress --dry-run=client -o yaml > ingress-svc.yml

kubectl create -f ingress-service.yml -n ingress-space

Sample ingress yaml which can be deployed against app