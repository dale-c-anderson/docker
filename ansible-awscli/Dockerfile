## Ansible + AWS CLI tools in a docker container!
## Loosely based on https://github.com/William-Yeh/docker-ansible/blob/master/ubuntu16.04/Dockerfile
FROM ubuntu:16.04
MAINTAINER Dale Anderson <danderson@acromediainc.com>


## Update apt
RUN apt-get -qq update


## Install Ansible
RUN echo "===> Adding Ansible's PPA..."  && \
    echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu xenial main" | tee /etc/apt/sources.list.d/ansible.list           && \
    echo "deb-src http://ppa.launchpad.net/ansible/ansible/ubuntu xenial main" | tee -a /etc/apt/sources.list.d/ansible.list    && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 7BB9C367    && \
    DEBIAN_FRONTEND=noninteractive  apt-get update  && \
    \
    \
    echo "===> Installing Ansible..."  && \
    apt-get install -y ansible  && \
    \
    \
    echo "===> Installing handy tools (not absolutely required)..."  && \
    apt-get install -y sshpass openssh-client  && \
    \
    \
    echo "===> Adding hosts for convenience..."  && \
    echo 'localhost' > /etc/ansible/hosts


## Install AWS Ec2 CLI tools
RUN apt-get install -yqq python-pip
RUN pip install -q awscli
RUN pip install -q yamllint
RUN pip install -q boto


## Set the default command: display Ansible version
CMD [ "ansible-playbook", "--version" ]
