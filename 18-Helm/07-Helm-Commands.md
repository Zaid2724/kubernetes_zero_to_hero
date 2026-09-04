# Important Helm Commands
Create Chart
helm create myapp
Install
helm install myapp ./myapp
List Releases
helm list

All namespaces:

helm list -A
Check Release
helm status myapp
Upgrade
helm upgrade myapp ./myapp
Upgrade with Values
helm upgrade myapp ./myapp \
-f values-prod.yaml
Uninstall
helm uninstall myapp
Rollback
helm rollback myapp 1
History
helm history myapp
Validate Chart
helm lint ./myapp
Render Templates
helm template myapp ./myapp
Dry Run
helm install myapp ./myapp --dry-run --debug