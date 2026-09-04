
# Helm Lifecycle

Install
   ↓
Upgrade
   ↓
Revision Created
   ↓
Upgrade
   ↓
Revision Created
   ↓
Rollback if required
Install
helm install myapp ./myapp
Upgrade
helm upgrade myapp ./myapp

Every successful upgrade creates a new revision.

Example:

Revision 1 → Initial deployment
Revision 2 → Image updated
Revision 3 → Replicas changed

Check:

helm history myapp

Rollback:

helm rollback myapp 1

This rolls the release back to Revision 1.