Using WSL 2 with Ubuntu 22.04 on Windows 11
- sudo apt update
- sudo apt upgrade -y
- # Try to see if the docker cli and daemon are installed
docker version
- # Same for kubectl
kubectl version
- If docker and kubectl are not installed:
    - Install Docker Desktop
    - In Setting --> General --> Enable Use WSL 2 based engine ( Activates docker for WSL)
    - In Setting --> Kubernetes --> Enable Kubernetes --> Select Kubeadm for main cluster (Activates kubectl for WSL)
    - This creates a node called docker-desktop in the WSL
- Debating if I have to install KinD or not
- Kubernetes Dashboard
    - # Install the Dashboard application into our cluster
        - kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc6/aio/deploy/recommended.yaml
    - # Check the resources it created based on the new namespace created
        - kubectl get all -n kubernetes-dashboard