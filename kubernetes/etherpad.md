Welcome to Etherpad Lite!

This pad text is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents!

Etherpad Lite on Github: http://j.mp/ep-lite

====================================================================================================
Day 1
====================================================================================================
Etherpad link: https://etherpad.openstack.org/p/k8s_workshop
Slide link:  https://docs.google.com/presentation/d/1117Qyk_XId5RSOF0ns10ZWssKzHflXMt8AUkRZSeaOE/edit?usp=sharing

Install Ingress in Docker Desktop (Window 10 pro)
- install prerequisite
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.27.0/deploy/static/mandatory.yaml
- install ingress controller
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.27.0/deploy/static/provider/cloud-generic.yaml

Resource:
Deployment
https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/nginx-deployment_foo.yaml
https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/nginx-deployment_bar.yaml

Service
https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/service_foo.yaml
https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/service_bar.yaml

Ingress
https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/ingress_foo.yaml
https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/ingress_bar.yaml




====================================================================================================
Day 2
====================================================================================================

Initial Setup
1. Launch 2 Instance with General2 C and B (2 CPU with Ram 4GB and 1 CPU with Ram 2GB) with Ubuntu 18.04
2. Disable Cloud firewall

#Step 3-6 Do every instance
3. SSH to Instance
4. $ sudo -i
5. # apt update -y
6. # apt upgrade -y

# In Master node
7. # git clone https://github.com/kubernetes-sigs/kubespray.git  /opt/kubespray
8. # ssh-keygen
9. # cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys 
10. # cat /root/.ssh/id_rsa.pub 
11. copy /root/.ssh/id_rsa.pub to worker node at /root/.ssh/authorized_keys
- At Worker node
$ nano /root/.ssh/authorized_keys
- paste publickey
- Ctrl + x , Y , Enter


Kubespray 
Install (Setup Cluster)
# cd /opt/kubespray/
# git checkout release-2.12
# apt install python3-pip python-pip python3-setuptools python-setuptools
# pip install -r requirements.txt
# cp -rfp inventory/sample inventory/csp_cluster
Get private IP from portal
# nano inventory/csp_cluster/inventory.ini
edit host in file with your instance ip https://github.com/ysirawit/k8s_workshop/blob/master/host_file.jpg
# nano inventory/csp_cluster/group_vars/k8s-cluster/addons.yml
edit  "helm_enabled: true" , "ingress_nginx_enabled: true"  ,  and save
# ansible-playbook -i inventory/csp_cluster/inventory.ini  -u root cluster.yml

Try:
    kubectl apply -f https://raw.githubusercontent.com/ysirawit/k8s_workshop/master/nginx-deployment.yaml


    
Scale Cluster
Launch 1 Instance with General2 B (1 CPU with Ram 2GB) with Ubuntu 18.04
Disable Cloud firewall

# In New worker node
SSH to Instance
$ sudo -i
$ apt update -y
$ apt upgrade -y

# In Master node
SSH to Master node
$ sudo -i
# cat /root/.ssh/id_rsa.pub 
copy /root/.ssh/id_rsa.pub to worker node at /root/.ssh/authorized_keys
- At Worker node 2
$ sudo nano /root/.ssh/authorized_keys
- paste publickey
- Ctrl + x , Y , Enter
# cd /opt/kubespray/
# nano inventory/csp_cluster/inventory.ini
add node3 and IP to [all]
add "node3" to [kube-node]  https://github.com/ysirawit/k8s_workshop/blob/master/scale-node-host.jpg
save file
# byobu
# ansible-playbook -i inventory/csp_cluster/inventory.ini  -u root scale.yml

Grafana
https://grafana.com/grafana/dashboards/6781

Kube Dashboard
https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/


