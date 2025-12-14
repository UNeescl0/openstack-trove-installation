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

## Step 1: Load OpenStack credentials
```bash
source admin-openrc.sh
## Step 2: Update system
sudo apt update && sudo apt upgrade -y
