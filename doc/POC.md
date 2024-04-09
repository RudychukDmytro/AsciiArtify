# Step-by-step instructions using kubectl

This manual describes the step-by-step installation, start-up, and authorization of the ArgoCD service.

## Installing ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

After installing the service, you can check its operation using the command:

```bash
kubectl get all -A
```

## Port forwarding for access from the host machine

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

You can now access ArgoCD at https://localhost:8080 on your host machine.

## Getting your login password

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
``` 

The output of this command will be the ArgoCD login password.

Default username is "admin"

Demo video: [https://www.loom.com/share/80bd03f42c8340789ee514ec08078b99](https://www.loom.com/share/80bd03f42c8340789ee514ec08078b99)
