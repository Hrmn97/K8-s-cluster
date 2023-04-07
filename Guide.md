1.) First we need docker engine in all the instance. Execute Docker.bash file

2.)PERFORM THIS IN ALL THREE INSTANCES

#swap memory off in all the instances
'''
sudo swapoff -a
free -h
sudo vi /etc/fstab # edit and comment out the swap files and images
'''


3.)NOW WE WILL INSTALL KUBECTL< KUBEADM< KUBELET IN ALL THE INSTANCES. Run the K8.bash file.

4.)BEFORE INTIALIZING KUBEADM IN MASTER PRFORM THEE IN ALL THE INSTANCES

'''
sudo apt remove containerd
sudo apt update
sudo apt install containerd.io
sudo rm /etc/containerd/config.toml
sudo systemctl restart containerd
'''

5.) INITIALIZING KUBEADM IN ADMIN ONLY
'''
kubeadm init --pod-network-cidr=10.244.0.0/16
'''

6.) COPY THE JOIN TOKEN SHOWN TO PASTE IT IN WORKER NODES AS LKE. IT WILL BE LIKE THIS KUBEADM JOIN <JOIN TOKEN>

7.) THERE ARE THREE COMMANDS SHOWN AFTER INITIALIZATION OF KUBEADM IN MASTER. RUN THEM ON MASTER ITSELF

8.) AND THEN CREATE FLANNEL NETWORK AS/ OR YOU CAN CHOOSE ANY NETWORK AVAILABLE
'''
kubectl apply -f https://github.com/coreos/flannel/raw/master/Documentation/kube-flannel.yml
'''

9.) '''kubectl get nodes'''
#ALL THE NODES SHOULD BE SHOWN READY