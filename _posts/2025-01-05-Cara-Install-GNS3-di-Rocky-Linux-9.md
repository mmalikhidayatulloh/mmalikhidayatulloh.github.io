```
sudo dnf update
sestatus
sudo sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config
sestatus
cat /etc/selinux/config
sudo grubby --update-kernel ALL --args selinux=0
sudo dnf install -y python3-devel elfutils-libelf-devel libpcap-devel python3-pyqt5-sip python3-qt5 xterm cmake busybox libnsl telnet\
sudo dnf groupinstall -y 'Development Tools'
cd /usr/local/src 
sudo mkdir gns3
cd gns3
sudo git clone https://github.com/GNS3/gns3-server.git
sudo git clone https://github.com/GNS3/gns3-gui.git
sudo git clone https://github.com/GNS3/vpcs.git
sudo git clone https://github.com/GNS3/dynamips.git
sudo git clone https://github.com/GNS3/ubridge.git
sudo python3 -m pip install --upgrade pip
cd /usr/local/src/gns3/gns3-server/
sudo pip3 install -r requirements.txt
sudo python3 setup.py install
cd /usr/local/src/gns3/gns3-gui/
sudo pip3 install -r requirements.txt
sudo python3 setup.py install
cd /usr/local/src/gns3/vpcs/src
sudo ./mk.sh
sudo cp vpcs /usr/local/bin/vpcs
cd /usr/local/src/gns3/dynamips/
sudo mkdir build 
cd build
cmake ..
sudo cmake ..
sudo make
sudo make install
cd /usr/local/src/gns3/ubridge
sudo make
sudo make install
sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf -y install docker-ce docker-ce-cli containerd.io
sudo systemctl enable --now docker
sudo usermod -aG docker "$(whoami)"
sudo grep -e 'vmx' /proc/cpuinfo
sudo dnf install -y bridge-utils virt-top libguestfs-tools bridge-utils virt-viewer qemu-kvm libvirt virt-manager virt-install
sudo usermod -aG libvirt "$(whoami)"\
sudo usermod -aG kvm "$(whoami)"\
sudo systemctl enable --now libvirtd\
sudo systemctl enable --now virtlogd
sudo git clone https://github.com/GNS3/gns3-registry.git /usr/local/share/gns3/gns3-registry
sudo chmod -R 777 /usr/local/share/gns3/gns3-registry
sudo sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/g' /etc/sysctl.conf
sudo sed -i 's/#net.bridge.bridge-nf-call-iptables=1/net.bridge.bridge-nf-call-iptables=1/g' /etc/sysctl.conf
sudo ln -s /usr/libexec/qemu-kvm /usr/bin/qemu-kvm
sudo firewall-cmd --permanent --add-port=3080/tcp
sudo firewall-cmd --reload
sudo dnf install -y xrdp
sudo systemctl enable --now xrdp
sudo firewall-cmd --permanent --add-port=3389/tcp
sudo firewall-cmd --reload
gns3server &
gns3
```
