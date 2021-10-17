# Change configuration cluster


## First command
```shell
cd 
cd install-kubernetes-lunanode
kubectl -n kube-system get configmap kubeadm-config -o jsonpath='{.data.ClusterConfiguration}' > kubeadm.yaml
```
## add IP address in kubeadm.yaml
```yaml
certSANs:
    - "172.20.15.146"
    - "51.254.227.45"
    - "k8s.domain.com"
    - "other-k8s.domain.net"
```

## Move existing certificates
```shell
mv /etc/kubernetes/pki/apiserver.{crt,key} ~
```
## Generate new certificates
```shell
sudo kubeadm init phase certs apiserver --config kubeadm.yaml # generate certificates
docker ps | grep kube-apiserver | grep -v pause  # get the container id 
docker kill <container-id>  # kill the docker container
sudo kubeadm init phase upload-config kubeadm --config kubeadm.yaml # upload new config
```
## get new kubeconfig file
kubectl config view --flatten --minify > cluster-cert.txt
