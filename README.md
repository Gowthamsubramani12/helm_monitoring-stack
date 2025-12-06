📦 Add Helm Repository
helm repo add monitoring https://Gowthamsubramani12.github.io/helm_monitoring-stack/


Verify repo:

helm repo list

🔄 Update Helm Repositories
helm repo update

🔍 Search for Chart
helm search repo monitoring


Result will look like:

monitoring/prom-stack-chart   0.1.0   A Helm chart for a complete monitoring stack

🚀 Install the Monitoring Stack

Namespace create (optional):

kubectl create ns monitoring


Install your chart:

helm install monitoring-stack monitoring/prom-stack-chart -n monitoring

🔧 Upgrade Release
helm upgrade monitoring-stack monitoring/prom-stack-chart -n monitoring


Or using custom values:

helm upgrade monitoring-stack monitoring/prom-stack-chart -n monitoring -f values.yaml

🧹 Uninstall / Delete Release
helm uninstall monitoring-stack -n monitoring


Optional: delete namespace

kubectl delete ns monitoring

📁 Check Installed Resources
helm list -n monitoring
kubectl get pods -n monitoring

♻️ Remove the Helm Repository
helm repo remove monitoring
