Terraform configuration files to provision an EKS cluster on AWS.

1. Launched a Test instance in personal AWS Account
2. Installed and configured required softwares in it such as git, terraform, helm, kubectl
3. configures aws credentials on the server which has access to create eks and dependant services
4. wrote terraform code to create eks cluster and considered to use modules from terraform registry
5. initialized terraform "terraform init"
6. checked for formatting and validated for errors
7. executed "terraform plan" to check on the resource that will be created, can be looked into tfstate file for more info
8. executed "terraform apply" to create the resources listed during terraform plan
9. the cluster was created including the 3 worker nodes as part of it
10. execute update-kubeconfig command to integrate the control node with the cluster
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)

11. [root@ip-172-31-24-242]# kubectl get nodes
NAME                         STATUS   ROLES    AGE   VERSION
ip-10-0-1-130.ec2.internal   Ready    <none>   19m   v1.20.11-eks-f17b81
ip-10-0-2-28.ec2.internal    Ready    <none>   19m   v1.20.11-eks-f17b81
ip-10-0-3-67.ec2.internal    Ready    <none>   19m   v1.20.11-eks-f17b81


