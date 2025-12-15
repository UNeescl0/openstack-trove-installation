# Trove Installation on OpenStack

##  Objective
This repository explains step by step how to install **Trove (Database as a Service)** on OpenStack.
This guide is for **beginners**.

---

## Prerequisites
- Ubuntu Server 22.04
- OpenStack installed (Kolla-Ansible or DevStack)
- Root or sudo access
- Python 3
- OpenStack client installed


# STEP 1: Load OpenStack credentials

```bash
source admin-openrc.sh
openstack token issue
```

# STEP 2: Update system

```bash
sudo apt update && sudo apt upgrade -y
```
moodify globals.yml
```bash
sudo nano /etc/kolla/globals.yml
```
```bash
enable_trove: "yes"
enable_haproxy: "yes"
```
# STEP 3: Install Trove packages

```bash
pip install python-troveclient

```

# STEP 4: créer un passwords.yml

```bash
cat > ~/openstack/passwords.yml <<EOF
admin_password: "Admin@123456"
database_password: "DB@123456"
message_queue_password: "MQ@123456"
rabbitmq_password: "RMQ@123456"
EOF


```
# lancer ton déploiement:
```bash
kolla-ansible deploy -i /home/user/openstack/all-in-one --passwords /home/user/openstack/passwords.yml
```

# STEP 5: Synchronize Trove database

```bash
sudo trove-manage db_sync
```

# STEP 6: Start and enable Trove services

```bash
sudo systemctl restart trove-api
sudo systemctl restart trove-taskmanager
sudo systemctl restart trove-conductor
sudo systemctl enable trove-api
sudo systemctl enable trove-taskmanager
sudo systemctl enable trove-conductor
```

# STEP 7: Verify Trove installation

```bash
bash sudo systemctl status trove-api
bash openstack database service list
```


