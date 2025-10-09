Using WSL 2 with Ubuntu 22.04 on Windows 11
- sudo apt update
- sudo apt upgrade -y
- Try to see if the docker cli and daemon are installed  
          *docker version*
- Same for kubectl  
*kubectl version*
- If docker and kubectl are not installed:
    - Install Docker Desktop
    - In Setting --> General --> Enable Use WSL 2 based engine ( Activates docker for WSL)
    - In Setting --> Kubernetes --> Enable Kubernetes --> Select Kubeadm for main cluster (Activates kubectl for WSL)
    - This creates a node called docker-desktop in the WSL
- Debating if I have to install KinD or not (update - no need at all)
- Kubernetes Dashboard
    - Install the Dashboard application into our cluster
        - *kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc6/aio/deploy/recommended.yaml*
    - Check the resources it created based on the new namespace created
        - *kubectl get all -n kubernetes-dashboard*
- *sudo apt install -y apt-transport-https ca-certificates curl*  
- *curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.31/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg*
- *echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list*
- *sudo apt update*
- *sudo apt install -y kubelet kubeadm kubectl*  
- *sudo kubeadm init*  

##########################################################################################################  
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  *mkdir -p $HOME/.kube*  
  *sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config*  
  *sudo chown $(id -u):$(id -g) $HOME/.kube/config*  

Alternatively, if you are the root user, you can run:

  *export KUBECONFIG=/etc/kubernetes/admin.conf*

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

*kubeadm join 172.21.235.254:6443 --token 9wz555.2qg8exxfb7m55sf1 --discovery-token-ca-cert-hash sha256:e6253f2343ff808bd5fda809e94e04b31b353bac0e93b6ede0240d824de23cc0*
