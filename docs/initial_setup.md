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

*kubeadm join 172.21.235.254:6443 --token 8i0vyi.9nlnas2wbhv4xayf --discovery-token-ca-cert-hash sha256:712d071887cb10fe3b0f6ac82ff4a251fd975c6f8293e828a30b9bebc0a57d45*
