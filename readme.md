# RBAC

REGION_CODE=us-east-1
CLUSTER_NAME=expense
ACC_ID=315069654700

### Permissions

* OIDC provider
```
eksctl utils associate-iam-oidc-provider \
    --region $REGION_CODE \
    --cluster $CLUSTER_NAME \
    --approve
```




User, Role, Rolebinding

expense-trainee --> read access to expense namespace

role should be bound to user --> through rolebinding

EKS is one platform, AWS is another platform

k8 has its own RBAC, AWS has its own

AWS integrates IAM service as authentication mechanism to EKS
a user should describe EKS to connect it..

1. create IAM user and provide describeEKSCluster access
2. we need to create role and rolebinding resources

aws-auth configmap need to be configured to connect EKS and IAM
mail suresh about his config is done, he can login

"" aws configure --profile raju "", using this command raju can connect to aws server

"" aws sts get-caller-identity --profile raju "", using this command we can check whether user suresh successfully log in or not to the server 

aws eks update-kubeconfig --region us-east-1 --name expense


kubectl get configmap aws-auth -n kube-system -o yaml ==> to get confgimap.yaml