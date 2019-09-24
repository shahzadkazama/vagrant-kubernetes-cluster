#variables

#Kubernetes Master installation all commands in one script
$script = <<-SCRIPT
yum install -y net-tools
MASTER_IP=`ifconfig |grep inet|grep 192| awk '{print $2}'|head -n 1`

echo Kubernetes Master provisioning...
setenforce 0
sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
swapoff -a
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install -y docker-ce

cat <<EOF >>/etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
	https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

echo '1' > /proc/sys/net/bridge/bridge-nf-call-iptables

yum install -y kubelet kubeadm kubectl
systemctl daemon-reload
systemctl restart kubelet
systemctl restart kubelet
systemctl start docker.service

kubeadm init --apiserver-advertise-address=$MASTER_IP --pod-network-cidr=192.168.1.0/16
sleep 30
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

/bin/kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
SCRIPT


#node script
$mynode = <<-NODESCRIPT
yum install -y net-tools
MASTER_IP=`ifconfig |grep inet|grep 192| awk '{print $2}'|head -n 1`

echo Kubernetes Master provisioning...
setenforce 0
sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
swapoff -a
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install -y docker-ce

cat <<EOF >>/etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
	https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
echo '1' > /proc/sys/net/bridge/bridge-nf-call-iptables
yum install -y kubelet kubeadm kubectl
systemctl daemon-reload
systemctl start docker.service
systemctl enable docker.service

NODESCRIPT




#starting vagrant config for vm provisioning
  Vagrant.configure("2") do |config|

    config.vm.define "master" do |master|
      master.vm.provision "shell", inline: $script
      master.vm.box = "centos/7"
      master.vm.hostname = 'master'
      master.vm.provider :libvirt do |libvirt|
        libvirt.cpus = 2
        libvirt.memory = 3000
        libvirt.cputopology :sockets => '2', :cores => '1', :threads => '1'
      end
    end


    config.vm.define "node" do |node|
      node.vm.provision "shell", inline: $mynode
      node.vm.box = "centos/7"
      node.vm.hostname = 'node1'
      node.vm.provider :libvirt do |libvirt|
        libvirt.cpus = 2
        libvirt.memory = 3000
        libvirt.cputopology :sockets => '2', :cores => '1', :threads => '1'
      end
    end


end
