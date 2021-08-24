# pgodemo

# Useful Links
JMeter:  https://jmeter.apache.org/download_jmeter.cgi
Crunchy Operator 5.0 Preview Doc:  https://pgo5-docs-preview.crunchydata.com/quickstart/

# Install ArgoCD
oc create namespace argocd
oc apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
oc patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
oc get secret -n argocd argocd-initial-admin-secret  --template={{.data.password}} | base64 -d

If not running on OpenShift or environment that does not have a load balancer:
kc patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'