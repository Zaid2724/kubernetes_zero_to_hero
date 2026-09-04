# Chart vs Release

Chart:

A package containing Kubernetes templates and configuration.

Release:

A running/installed instance of a Chart.

Example:

Chart
  ↓

nginx-chart

  ↓ helm install

Release
  ↓

my-nginx

You can install the same Chart multiple times:

nginx-chart
   │
   ├── Release: nginx-dev
   ├── Release: nginx-test
   └── Release: nginx-prod
Easy Memory Trick
Chart = Blueprint

Release = Installed Application