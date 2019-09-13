# vagrant-kubernetes-cluster
vagrantfile to install kubernets cluster of two nodes verified on ubuntu 18


<b>Steps:</b>

1- install virtual box <br/>
&nbsp;&nbsp;&nbsp;&nbsp;sudo apt update
&nbsp;&nbsp;&nbsp;&nbsp;sudo apt upgrade
&nbsp;&nbsp;&nbsp;&nbsp;wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
&nbsp;&nbsp;&nbsp;&nbsp;wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
&nbsp;&nbsp;&nbsp;&nbsp;sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"
&nbsp;&nbsp;&nbsp;&nbsp;sudo apt update
&nbsp;&nbsp;&nbsp;&nbsp;sudo apt install virtualbox-6.0

2- install sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"

vagrant  <br/>
3- clone this project and execute Vagrant file <br/>
  &nbsp;&nbsp;&nbsp;&nbsp; -> git clone https://github.com/shahzadkazama/vagrant-kubernetes-cluster.git <br/>
  &nbsp;&nbsp;&nbsp;&nbsp; -> cd vagrant-kubernetes-cluster <br/>
  &nbsp;&nbsp;&nbsp;&nbsp; -> vagrant up <br/>
  
