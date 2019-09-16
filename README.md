# vagrant-kubernetes-cluster
vagrantfile to install kubernets cluster of two nodes verified on ubuntu 18


<b>Steps:</b>

<b>1- install virtual box <br/></b>
<i>
 
<code>&nbsp;&nbsp;&nbsp;&nbsp;sudo apt update   </code> <br/><br/>
<code> &nbsp;&nbsp;&nbsp;&nbsp;sudo apt upgrade  </code> <br/><br/>
<code> &nbsp;&nbsp;&nbsp;&nbsp;wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add - </code> <br/> <br/>
<code> &nbsp;&nbsp;&nbsp;&nbsp;wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add - </code> <br/> <br/>
<code> &nbsp;&nbsp;&nbsp;&nbsp;sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib" </code> <br/> <br/>
<code>&nbsp;&nbsp;&nbsp;&nbsp;sudo apt update </code> <br/> <br/>
<code> &nbsp;&nbsp;&nbsp;&nbsp;sudo apt install virtualbox-6.0 </code> <br/><br/>

 </i>

<b>2- install vagrant  <br/></b><br/>
<code>&nbsp;&nbsp;&nbsp;&nbsp; sudo apt install vagrant </code> <br/> <br/>
<b>3- clone this project and execute Vagrant file <br/></b> <br/>
<i>
  <code>&nbsp;&nbsp;&nbsp;&nbsp; -> git clone https://github.com/shahzadkazama/vagrant-kubernetes-cluster.git </code> <br/> <br/>
  <code>&nbsp;&nbsp;&nbsp;&nbsp; -> cd vagrant-kubernetes-cluster </code><br/><br/>
  <code>&nbsp;&nbsp;&nbsp;&nbsp; -> vagrant up </code><br/><br/>
 </i>
