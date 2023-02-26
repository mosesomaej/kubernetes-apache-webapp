<!-- Run the EKS cluster without nodegroup using default settings. -->
eksctl create cluster --name playgound --region us-west-2 --version 1.24  --without-nodegroup
<!-- Run the node group -->
eksctl create nodegroup \
  --cluster playground-cluster \
  --region us-west-2 \
  --name playground-ng \
  --node-ami-family AmazonLinux2 \
  --node-type m5.large \
  --nodes 3 \
  --nodes-min 3 \
  --nodes-max 4 \
  --ssh-access \
  --ssh-public-key us-west2-key
<!-- Create a deployment for Apache webserver -->
