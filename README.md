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

---


---

## ✅ EXEMPLE FINAL (COPIE EXACTEMENT)

⚠️ **TRÈS IMPORTANT : tu dois copier AUSSI les ```**

```markdown
```bash
# ================================
# STEP 1: Load OpenStack credentials
# ================================
source admin-openrc.sh
openstack token issue

# ================================
# STEP 2: Update system
# ================================
sudo apt update && sudo apt upgrade -y

# ================================
# STEP 3: Install Trove packages
# ================================
sudo apt install -y trove-api trove-taskmanager trove-conductor python3-troveclient

# ================================
# STEP 4: Configure Trove
# ================================
sudo nano /etc/trove/trove.conf
# Configure:
# - Database connection
# - RabbitMQ
# - Keystone authentication
# - Neutron networking

# ================================
# STEP 5: Synchronize Trove database
# ================================
sudo trove-manage db_sync

# ================================
# STEP 6: Start and enable Trove services
# ================================
sudo systemctl restart trove-api
sudo systemctl restart trove-taskmanager
sudo systemctl restart trove-conductor
sudo systemctl enable trove-api
sudo systemctl enable trove-taskmanager
sudo systemctl enable trove-conductor

# ================================
# STEP 7: Verify Trove installation
# ================================
sudo systemctl status trove-api
openstack database service list
