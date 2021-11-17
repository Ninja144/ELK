# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
 
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

#Kibana

#node01
  config.vm.define "kibananode01" do |kibananode01|
    kibananode01.vm.box = "centos/7"
    kibananode01.vm.network "private_network", ip: "10.0.3.2"
    kibananode01.vm.hostname = "kibana-node01"
    kibananode01.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end
    kibananode01.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      systemctl stop firewalld
      systemctl disable firewalld
      sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
      setenforce 0
      yum install -y vim bash-completion mc bind-utils
      cat > /etc/resolf.conf << EOF
nameserver 8.8.8.8
EOF
      cat > /etc/hosts << EOF
127.0.0.1   localhost kibana-node01
10.0.3.11   es-node01
10.0.3.12   es-node02
10.0.3.13   es-node03
10.0.3.21   logstash-node01
EOF
    SHELL
  end

#Elasticsearch

#node01
  config.vm.define "esnode01" do |esnode01|
    esnode01.vm.box = "centos/7"
    esnode01.vm.network "private_network", ip: "10.0.3.11"
    esnode01.vm.hostname = "es-node01"
    esnode01.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end
    esnode01.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      systemctl stop firewalld
      systemctl disable firewalld
      sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
      setenforce 0
      yum install -y vim bash-completion mc bind-utils
      cat > /etc/resolf.conf << EOF
nameserver 8.8.8.8
EOF
      cat > /etc/hosts << EOF
127.0.0.1   localhost es-node01
10.0.3.2    kibana-node01
10.0.3.12   es-node02
10.0.3.13   es-node03
10.0.3.21   logstash-node01
EOF
    SHELL
  end

#node02
  config.vm.define "esnode02" do |esnode02|
    esnode02.vm.box = "centos/7"
    esnode02.vm.network "private_network", ip: "10.0.3.12"
    esnode02.vm.hostname = "es-node02"
    esnode02.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end
    esnode02.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      systemctl stop firewalld
      systemctl disable firewalld
      sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
      setenforce 0
      yum install -y vim bash-completion mc bind-utils
      cat > /etc/resolf.conf << EOF
nameserver 8.8.8.8
EOF
      cat > /etc/hosts << EOF
127.0.0.1   localhost es-node02
10.0.3.2    kibana-node01
10.0.3.11   es-node01
10.0.3.13   es-node03
10.0.3.21   logstash-node01
EOF
    SHELL
  end

#node03
  config.vm.define "esnode03" do |esnode03|
    esnode03.vm.box = "centos/7"
    esnode03.vm.network "private_network", ip: "10.0.3.13"
    esnode03.vm.hostname = "es-node03"
    esnode03.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end
    esnode03.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      systemctl stop firewalld
      systemctl disable firewalld
      sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
      setenforce 0
      yum install -y vim bash-completion mc bind-utils
      cat > /etc/resolf.conf << EOF
nameserver 8.8.8.8
EOF
      cat > /etc/hosts << EOF
127.0.0.1   localhost es-node03
10.0.3.2    kibana-node01
10.0.3.11   es-node01
10.0.3.12   es-node02
10.0.3.21   logstash-node01
EOF
    SHELL
  end

#Logstash

#node01
  config.vm.define "logstashnode01" do |logstashnode01|
    logstashnode01.vm.box = "centos/7"
    logstashnode01.vm.network "private_network", ip: "10.0.3.21"
    logstashnode01.vm.hostname = "logstash-node01"
    logstashnode01.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end
    logstashnode01.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      systemctl stop firewalld
      systemctl disable firewalld
      sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
      setenforce 0
      yum install -y vim bash-completion mc bind-utils
      cat > /etc/resolf.conf << EOF
nameserver 8.8.8.8
EOF
      cat > /etc/hosts << EOF
127.0.0.1   localhost logstash-node01
10.0.3.2    kibana-node01
10.0.3.11   es-node01
10.0.3.12   es-node02
10.0.3.13   es-node03
EOF
    SHELL
  end

end
