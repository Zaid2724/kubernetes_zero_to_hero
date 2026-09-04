# Helm Dependencies

One Helm Chart can depend on another Chart.

Example:

Application
     │
     ├── MySQL
     └── Redis

Define dependencies in:

Chart.yaml

Example:

dependencies:
  - name: redis
    version: "20.x.x"
    repository: "https://example.com/charts"

Update dependencies:

helm dependency update

Dependencies are stored locally in:

charts/