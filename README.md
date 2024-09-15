# infra-prod-cluster

This holds the Kubernetes files for the infra-prod Kubernetes cluster in Digital Ocean.

## FluxCD

To bootstrap this FluxCD repo to a cluster, run the following command. A GitLab project access token must be provided.
It should have the `maintainer` role and `api` access. This is because FluxCD sometime has to write to the repository.

```bash
flux bootstrap gitlab \
          --components-extra=image-reflector-controller,image-automation-controller \
          --hostname=https://gitlab.login.no \
          --owner=tekkom/infrastructure/kubernetes \
          --repository=infra-prod-cluster \
          --branch=main \
          --path=cluster/ \
          --deploy-token-auth
```

