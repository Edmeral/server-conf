# Linux User Creation with Passwordless Sudo

## Overview
Created a new user `aissam` with passwordless sudo access and Docker privileges on the system.

## Date
December 7, 2025

## Steps Performed

### 1. Create the User (to be done on root)
```bash
sudo adduser aissam
echo "aissam ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/aissam
sudo chmod 0440 /etc/sudoers.d/aissam
```

### 2. Copy Files from Root Directory
```bash
sudo cp -r /root/somefile /home/aissam/
sudo chown -R aissam:aissam /home/aissam/somefile
```

### 3. Enable Docker Access Without Sudo
```bash
sudo usermod -aG docker aissam
```

### 4. Run the playbook (with uvx)
```bash
uvx --from ansible-core ansible-playbook playbook.yml -i inventory.yml

# To just check if everything would run without actually running it
uvx --from ansible-core ansible-playbook playbook.yml --check -i inventory.yml 
```
