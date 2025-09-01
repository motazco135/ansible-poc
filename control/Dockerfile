FROM python:3.12-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    openssh-client sshpass curl ca-certificates git jq \
 && rm -rf /var/lib/apt/lists/*

# Install Ansible
RUN pip install ansible

# Non-root user (optional)
RUN useradd -ms /bin/bash ansible && mkdir -p /home/ansible/.ssh && chown -R ansible:ansible /home/ansible
USER ansible
WORKDIR /workspace

CMD ["sleep", "infinity"]