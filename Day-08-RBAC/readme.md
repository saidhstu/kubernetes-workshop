# copy keys from master to management server - ca.crt - ca.key

# Create User user1

openssl genrsa -out user1.key 2048
openssl req -new -key user1.key -out user1.csr -subj "/CN=user1/O=development"
openssl x509 -req -in user1.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out user1.crt -days 365

# Here we are signing the key with Certificate Authority

# Create User adminstrator

openssl genrsa -out user2.key 2048
openssl req -new -key user2.key -out user2.csr -subj "/CN=user2/O=production"
openssl x509 -req -in user2.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out user2.crt -days 365


# Create User user1

openssl genrsa -out saidur.key 2048
openssl req -new -key saidur.key -out saidur.csr -subj "/CN=saidur/O=clusteradmin"
openssl x509 -req -in saidur.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out saidur.crt -days 365

# Here we are signing the key with Certificate Authority

# Now copy all .crt and .key to master root location safely.
 Now copy all .crt and .key to master root location safely.
---
create config file for both user on master
export KUBECONFIG=/root/USER1-CONFIG
export KUBECONFIG=/root/SAIDUR-CONFIG
---
create role for both and deploy
---
Bindings

ClusterRolebinding 
KUBECONFIG=USER1-CONFIG:USER2-CONFIG:SAIDUR-CONFIG kubectl config view --merge --flatten > mixed-config.txt

export KUBECONFIG=/root/mixed-config.txt
 
 1. find / -name crt
 2. find / -name kops-controller
 /etc/kubernetes/kops-controller

