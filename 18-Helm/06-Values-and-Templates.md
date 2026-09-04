# Values and Templates

Helm replaces dynamic values inside templates.

values.yaml:

replicaCount: 3

Template:

spec:
  replicas: {{ .Values.replicaCount }}

After rendering:

spec:
  replicas: 3
Override Values

Command:

helm install myapp ./myapp \
--set replicaCount=5

Result:

Default value: 3

Override value: 5

Use another values file:

helm install myapp ./myapp \
-f values-prod.yaml
Common Template Variables
.Values      → values.yaml

.Release     → release information

.Chart       → chart information

.Template    → template information

Example:

name: {{ .Release.Name }}

If the release name is:

myapp

Result:

name: myapp