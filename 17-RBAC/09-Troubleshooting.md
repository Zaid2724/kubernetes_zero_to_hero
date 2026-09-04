# RBAC Troubleshooting

## Check Roles

kubectl get roles -n development

kubectl describe role <role-name> -n development
Check ClusterRoles
kubectl get clusterroles
Check RoleBindings
kubectl get rolebindings -n development
Check ClusterRoleBindings
kubectl get clusterrolebindings
Check Permissions

One of the most useful commands:

kubectl auth can-i get pods -n development

Check another action:

kubectl auth can-i delete pods -n development

Check as another user:

kubectl auth can-i get pods \
--as=developer1 \
-n development

Result:

yes

or:

no
Common Error
Error from server (Forbidden)

Possible reasons:

Role does not contain the required verb.
Wrong resource is configured.
RoleBinding is missing.
Wrong Namespace.
Wrong ServiceAccount.
RoleBinding references the wrong Role.