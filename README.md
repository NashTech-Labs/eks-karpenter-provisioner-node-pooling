## Prerequisites
1) EKS Cluster
2) Karpenter on eks cluster

## Karpenter Provisioner Deployment (with Node Pooling)
- https://karpenter.sh/v0.8.0/provisioner/
- https://blog.mikesir87.io/2022/01/creating-tenant-node-pools-with-karpenter/

- After the cluster is up and running, we create mutators and provisioners

```Bash
helm repo add gatekeeper https://open-policy-agent.github.io/gatekeeper/charts
helm install gatekeeper/gatekeeper --name-template=gatekeeper --namespace gatekeeper-system --create-namespace
cd mutators_provisioners
kubectl apply -f karpenter-provisioner.yaml
```

---

## Helpful Commands
kubectl logs -f -n karpenter -l app.kubernetes.io/name=karpenter -c controller
```