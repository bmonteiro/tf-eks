```bash
#build
cd examples/karpenter
terraform init
terraform plan
terraform apply --auto-approve

kubectl apply -f inflate.yaml

kubectl logs -f -n kube-system -l app.kubernetes.io/name=karpenter -c controller

#destroy
kubectl delete deployment inflate
terraform destroy --auto-approve

kubectl config delete-context arn:aws:eks:eu-central-1:<ACCOUNT ID>:cluster/ex-karpenter
kubectl config delete-cluster arn:aws:eks:eu-central-1:<ACCOUNT ID>:cluster/ex-karpenter
kubectl config delete-user arn:aws:eks:eu-central-1:<ACCOUNT ID>:cluster/ex-karpenter
```
