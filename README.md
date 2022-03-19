How to use this (Setup Instructions):

1. Make your servers ready (one master node and multiple worker nodes).
2. Make an entry of your each hosts in /etc/hosts file for name resolution.
3. Make sure kubernetes master node and other worker nodes are reachable between each other.

4. Internet connection must be enabled in all nodes, required packages will be downloaded from kubernetes official yum repository.
5. Clone this repository into your master node.
   
   git clone https://github.com/TusherGhosh/kubernetes_ansible.git or download zip file kubernetes_ansible-main.zip (only this file)
   once it is cloned, get into the directory
   
   cd kubernetes-and-ansible/centos

6. There is a file "hosts" available in "centos" directory, Just make your entries of your all kubernetes nodes. 
7. Provide your server details in "env_variables" available in "centos" directory.
8. Deploy the ssh key from master node to other nodes for password less authentication.

   ssh-keygen
   
   Copy the public key to all nodes including your master node and make sure you are able to login into any nodes without password.
   
9. Run "settingup_kubernetes_cluster.yml" playbook to setup all nodes and kubernetes master configuration.

   ansible-playbook settingup_kubernetes_cluster.yml
   
10. Run "join_kubernetes_workers_nodes.yml" playbook to join the worker nodes with kubernetes master node once "settingup_kubernetes_cluster.yml" playbook tasks are completed.

      ansible-playbook join_kubernetes_workers_nodes.yml

11. Verify the configuration from master node.

      kubectl get nodes
