# Cloud image Proxmox template

## Prerequisites
```
apt-get install libguestfs-tools python3-pip python3-venv
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Create template VM
```
source .venv/bin/activate
./scripts/create-template-vm
```

## Clone template VM
```
qm clone 9000 100 --name dns
qm set 100 --ipconfig0 ip=10.0.100.11/24,gw=10.0.100.1
qm set 100 --memory 2048
qm set 100 --cores 2
qm set 100 --autostart 1
qm resize 100 scsi0 8G
qm start 100 && qm terminal 100
```
