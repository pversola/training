https://drive.google.com/drive/folders/1c4HUlz1Av8K5g4Z0etsytkvSN2FqHRMr?usp=sharing

https://docs.ceph.com/docs/master/mgr/prometheus/


https://github.com/ceph/ceph-ansible

https://docs.ceph.com/ceph-ansible/master/

Ceph 

RGW >> s3 upload file
MON >> Monitor and manament
OSD >> Disk
MGR >> Dashboard amd Metric

https://github.com/liwsakilive/ceph-workshop-cs100

git clone https://github.com/liwsakilive/ceph-workshop-cs100.git

ssh nc-user@139.5.147.44
ssh nc-user@139.5.147.145
ssh nc-user@
password : Aa123456++

sudo -i
ceph -s
ceph -w
ceph osd tree
ceph osd ls
ceph osd pool ls



Create 3 VM
 - Password
 - Cloud Firewall : ALL
 - 3 VM
 - Disable : Autobackup
Volume 3 disk



Emai :  paisit.k@chanwanich.com /
Email : aon_samprsn@hotmail.com /
Email: chairat.w@chanwanich.com /
Email: nirapan.n@chanwanich.com /
Email : danupon.b@chanwanich.com /
Email :chankrit.tasripu@gmail.com /
Email : thanakrit.s@chanwanich.com /
Email : sakkarin.s@chanwanich.com /

http://139.5.147.44:7000/
http://139.5.147.44:9283/metrics

(All Node)
sudo apt-get update
sudo apt-get install htop iftop nmon -y

(run node 1 only )
sudo -i
git clone https://github.com/liwsakilive/ceph-workshop-cs100.git
sudo add-apt-repository ppa:ansible/ansible-2.4
sudo apt-get update -y && apt-get install ansible python-pip python-netaddr -y
byobu
lsblk
cd /root/ceph-workshop-cs100/group_vars
vim rgws.yml
vim all.yml
vim /root/ceph-workshop-cs100/host_vars/ceph-cluster-node-1.yml
vim /root/ceph-workshop-cs100/host_vars/ceph-cluster-node-2.yml
cp /root/ceph-workshop-cs100/host_vars/ceph-cluster-node-2.yml /root/ceph-workshop-cs100/host_vars/ceph-cluster-node-3.yml 
vim ceph-cluster.ini
ansible --version
ansible-playbook -i ceph-cluster.ini site.yml -Kk --check

cd /root/ceph-workshop-cs100
ansible-playbook -i ceph-cluster.ini site.yml -Kk

apt-get install unzip
wget https://github.com/liwsakilive/ceph-workshop-cs100/archive/master.zip
unzip master.zip


ceph -s
ceph -w
ceph osd tree
ceph osd ls
ceph osd pool ls

ceph osd pool set .rgw.root pg_num 200
ceph osd pool set .rgw.root pgp_num 200
ceph health detail

cat ceph-workshop-cs100/ceph-cluster.ini
ansible-playbook -i ceph-cluster.ini site.yml -Kk --limit mons

watch -n 0.1 ceph -s
ceph mgr module enable dashboard

cp ceph-cluster-node-1.yml ceph-cluster-node-4.yml
lsblk

#### install ceph-client ####
sudo apt-get update -y
sudo apt-get install ceph-fuse

#### Ceph mon #####
cd /etc/ceph/
cat ceph.conf
cat ceph.client.admin.keyring

#### client #####
mkdir /etc/ceph/

# copy /etc/ceph/ceph.conf from ceph mon to client
vim /etc/ceph/ceph.conf

# copy /etc/ceph/ceph.client.admin.keyring from ceph mon to client
vim /etc/ceph/ceph.client.admin.keyring

mkdir /mnt/cephfs
ceph-fuse -m 10.148.0.18 /mnt/cephfs

wget http://mirrors.bangmod.cloud/centos/8.1.1911/isos/x86_64/CentOS-8.1.1911-x86_64-dvd1.iso

#### Day 2

#### remove ceph mon node
ceph mon rm liwsaki-workshop-3

#### Step remove osd
ceph osd set noout
ceph osd set norebalance
ceph osd primary-affinity osd. 0
ceph osd out osd.0
ceph osd down osd.0
systemctl stop ceph-osd@0.service
ceph osd crush reweight osd. 0
ceph osd rm osd.0 ## or ceph osd purge osd.0
ceph osd crush rm osd.0
ceph auth del osd.0
ceph osd crush rm ceph-workshop-1
ceph osd unset norebalance

ceph health detail

############### Start Day2 Deploy ##############

#### Deploy from offical

# ubuntu
apt update
apt install python python-pip sshpass

git clone https://github.com/liwsakilive/ceph-ansible-4.git
git clone https://github.com/ceph/ceph-ansible.git
cd ceph-ansible
git checkout v4.0.14

pip install setuptools
pip install -r requirements.txt


vim /root/ceph-ansible-4/ceph-cluster.ini

[mons]
ceph-cluster-node-1 ansible_host=139.5.146.57 ansible_user=nc-user
ceph-cluster-node-2 ansible_host=139.5.146.75 ansible_user=nc-user
ceph-cluster-node-3 ansible_host=139.5.146.229 ansible_user=nc-user

[osds]
ceph-cluster-node-1 ansible_host=139.5.146.57 ansible_user=nc-user
ceph-cluster-node-2 ansible_host=139.5.146.75 ansible_user=nc-user
ceph-cluster-node-3 ansible_host=139.5.146.229 ansible_user=nc-user

[mgrs]
ceph-cluster-node-1 ansible_host=139.5.146.57 ansible_user=nc-user
ceph-cluster-node-2 ansible_host=139.5.146.75 ansible_user=nc-user
ceph-cluster-node-3 ansible_host=139.5.146.229 ansible_user=nc-user

[rgws]
ceph-cluster-node-1 ansible_host=139.5.146.57 ansible_user=nc-user
ceph-cluster-node-2 ansible_host=139.5.146.75 ansible_user=nc-user
ceph-cluster-node-3 ansible_host=139.5.146.229 ansible_user=nc-user

[all:children]
mons
osds
mgrs
rgws

cd /root/ceph-ansible
ansible-playbook -i ../ceph-ansible-4/ceph-cluster.ini site.yml.sample -Kk

 ceph --version
 
 ceph osd lspools
 
 ceph osd tree
 
 sudo timedatectl set-timezone Asia/Bangkok

#### Monitor ####

ceph device ls

ceph mgr module enable pg_autoscaler

ceph mgr module enable dashboard 
ceph mgr module ls 

sudo ceph dashboard create-self-signed-cert 
### Self-signed certificate created 

ceph dashboard ac-user-create liwsakilive P@ssw0rd1 administrator


http://139.5.147.204:8443/#/dashboard

ceph osd pool set .rgw.root pg_autoscale_mode on

ceph osd pool autoscale-status

#### RGW user ####

radosgw-admin user create --uid=liwsakilive --display-name=liwsakilive \
    --system

radosgw-admin user info --uid=liwsakilive

ceph dashboard set-rgw-api-access-key <key>
ceph dashboard set-rgw-api-secret-key <key> 

ceph dashboard set-rgw-api-port 8080 #### rados port
ceph dashboard set-rgw-api-host <ip> #### IP rados


global:
  scrape_interval:     15s
  evaluation_interval: 15s

scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: 'prometheus'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
    - targets: ['139.5.144.4:9283']
    
    
git clone https://github.com/robtec/prometheus-grafana.git
cd prometheus-grafana
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose up -d

ceph osd pool ls detail
ceph osd pool set cephfs_data size 3
ceph osd df 

Optional:
ceph mgr module enable dashboard ## xxx.xxx.xxx.xxx:7000
ceph mgr module enable prometheus  ## xxx.xxx.xxx.xxx:9283    

ceph osd pool get-quota cephfs_data

vim /etc/hosts
docker ps

