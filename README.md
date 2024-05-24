# K8-s-setup
# K8-s-setup

1)first create master and worker nodes as per your requirment

than run 1.sh on all machines.

2) good job ! you did it :-) and now run this few commands8. Configure Kubernetes Cluster [On MasterNode]
 

3)  Update Package List[On Master & Worker Node]

   sudo apt update 

4)  Install Kubernetes Components[On Master & Worker Node]  {versions as per compatibilty}

 sudo apt install -y kubeadm=1.28.1-1.1 kubelet=1.28.1-1.1 kubectl=1.28.1-1.1

5)  Initialize Kubernetes Master Node [On MasterNode]

  sudo kubeadm init --pod-network-cidr=10.244.0.0/16

6)  Configure Kubernetes Cluster [On MasterNode]
 
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

7)  Deploy Networking Solution (Calico) [On MasterNode]

  kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml

8)  Deploy Ingress Controller (NGINX) [On MasterNode]

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.49.0/deploy/static/provider/baremetal/deploy.yaml


 
