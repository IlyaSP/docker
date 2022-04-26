FROM python:3.9.6-slim

RUN apt-get -y update \
    && apt-get  install -y --no-install-recommends ca-certificates \
    nano openssh-server iputils-ping sshpass telnet curl git gnupg lsb-release  \
    && pip3 install ansible paramiko molecule[docker] yamllint ansible-lint flake8 \
    && apt-get purge -y gcc \
    && apt-get -y autoremove && apt-get -y clean \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

  RUN apt-get -y update \
      && apt-get  install -y --no-install-recommends docker-ce docker-ce-cli containerd.io \
      && apt-get -y autoremove && apt-get -y clean \
      && rm -rf /var/lib/apt/lists/*

#RUN pip3 install ansible paramiko molecule[docker] yamllint ansible-lint flake8

ENV ANSIBLE_HOST_KEY_CHECKING=False

RUN ansible-galaxy collection install -v community.docker:>=1.9.1

#COPY ansible.cfg /etc/ansible/ansible.cfg

