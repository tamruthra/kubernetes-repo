eksctl commands and pre-requisite to create the cluster
-------------------------------------------------------
Pre-requiste software:
1. eksctl installation link - https://github.com/eksctl-io/eksctl/blob/main/README.md#installation
2. kubectl - https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

Step 1: Create the cluster
# eksctl create cluster -f eks-priv-cluster-conf.yaml

Step 2: Update the kubeconfig to connect the cluster
# aws eks update-kubeconfig --name eks-demo --region us-west-2

Step 3: Find the cluster details
# eksctl get cluster --region us-west-2
      or
# kubectl cluster-info

Step 4: Find the nodegroups and nodes
# eksctl get nodegroups --cluster eks-demo --region us-west-2
    or
# kubectl get nodes -o wide

Step 5: Authorise the oidc provider and after the below step check in the IAM -> Identity provider section
#  eksctl utils associate-iam-oidc-provider --cluster eks-demo --region us-west-2
#  eksctl utils associate-iam-oidc-provider --cluster eks-demo --region us-west-2 --approve

Step 6: To delete the cluster
# eksctl delete cluster -f eks-priv-cluster-conf.yaml
