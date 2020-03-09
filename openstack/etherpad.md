http://139.5.147.178/os100/
https://etherpad.openstack.org/p/os100atNipa

tumtarm2533

http://139.5.147.178/single_server_basic.yml
http://139.5.147.178/heat.yaml
//new heat template
http://139.5.147.178/os100/


 sudo systemctl  status iscsid


http://download.cirros-cloud.net/0.4.0/cirros-0.4.0-x86_64-disk.img



silde and lab
https://www.dropbox.com/s/o8pu7ymfy73bljp/os100-R.zip?dl=0


103.74.254.37 patrick
103.74.255.176 game
103.74.255.197 Nuttawut
103.74.255.124 pimarn
103.74.254.185sakkarin
103.74.255.74nirapan
139.5.144.54 somboon
139.5.144.14 chairat
139.5.144.20 paisit
139.5.144.32danupon



https://unix.stackexchange.com/questions/199164/error-run-lvm-lvmetad-socket-connect-failed-no-such-file-or-directory-but




https://docs.mirantis.com/mcp/q1-18/mcp-ref-arch/_downloads/mcp_compute_sizing.xlsx

'
https://unix.stackexchange.com/questions/199164/error-run-lvm-lvmetad-socket-connect-failed-no-such-file-or-directory-but

852
systemctl restart lvm2-lvmetad.service

http://cloudinit.readthedocs.io/en/latest/topics/examples.html




username: stack
password: b00tcamp


demo
nova



$ sudo -i
# apt-get update
# apt-get dist-upgrade
# reboot

--- re-login form ssh ---

$ sudo -i
# byobu
# apt install virtualenv -y
# git clone https://opendev.org/openstack/openstack-ansible     /opt/openstack-ansible
# cd /opt/openstack-ansible/
# git checkout 20.0.1
# ./scripts/bootstrap-ansible.sh
# ./scripts/bootstrap-aio.sh
# cd /opt/openstack-ansible/playbooks
# openstack-ansible setup-hosts.yml   
# openstack-ansible setup-infrastructure.yml  
# openstack-ansible setup-openstack.yml

# cd ~
# cat openrc


systemctl start iscsid

/etc/ssh/ssd_co




useradd -s /bin/bash -d /opt/stack -m stack
echo "stack ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
passwd stack
vim /etc/hosts
su - stack
git clone https://git.openstack.org/openstack-dev/devstack
cd devstack/
git checkout stable/rocky
vim local.conf
...
52 HOST_IP_IFACE=ens160
...

byobu
cd /opt/stack/devstack
