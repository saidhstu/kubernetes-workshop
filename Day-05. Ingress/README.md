sudo snap install --classic certbot

sudo certbot certonly --manual --preferred-challenges=dns --key-type rsa --email <email> \
--server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d *.srdevops.co


kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.3.1/deploy/static/provider/aws/deploy.yaml


kubectl create secret tls nginx-tls-default --key="tls.key" --cert="tls.crt"
docker Secret

kubectl create secret docker-registry docker-pwd --docker-username=<username> --docker-password=<dckr_pat_L> --docker-email=<email>
 
