# My Ansible

## Project Setup

Create a `.env` file in `./ansible/playbooks/templates/dns_server/`

## Ansible hosts file

The Ansible hosts file is in `./config` directory. Update this file with your hosts. You can change this after the image build.

## Playbooks

### Base Setup

The playbook will configure the remote servers ssh service to allow just ssh connection with your host ssh keys. Make sure you have a back up.

Run the container:

```bash
docker compose run --rm app bash
```

For every linux server execute `linux_server_init_setup` playbook with the user:
```bash
ansible-playbook linux_server_init_setup.yml -l orangepi -u orangepi -kK
```

Now you can access your server without need a password.

### DNS Server

In my homelab the oragepi will be the host of my dns server. For this, the next playbook will do two things:

 - Configure a fixed IP for orange pi
 - Install pihole and unbound

After that we need go to `hosts` file and change the orangepi IP.

```bash
ansible-playbook install_dns_server.yml
```
### Reverse Proxy

I'm using Traefik to do the job.

```bash
ansible-playbook install_reverse_proxy_service.yml
```

### Monitoring

I'm using Prometheus and Grafana to monitor my services.

```bash
ansible-playbook install_monitoring_service.yml
```

### Dashboard

```bash
ansible-playbook install_homepage.yml
```

### Home Assistant

```bash
ansible-playbook install_homeassistant.yml
```

### N8N

```bash
ansible-playbook install_n8n.yml
```