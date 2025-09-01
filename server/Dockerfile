FROM debian:stable-slim


RUN apt-get update && apt-get install -y --no-install-recommends \
    openssh-server curl ca-certificates sudo python3 \
 && rm -rf /var/lib/apt/lists/*

# Create ansible user with passwordless sudo
RUN useradd -ms /bin/bash ansible && echo "ansible ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ansible && chmod 440 /etc/sudoers.d/ansible

# SSH setup
RUN mkdir -p /var/run/sshd /home/ansible/.ssh /data/staging /data/target \
 && chown -R ansible:ansible /home/ansible /data


EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]