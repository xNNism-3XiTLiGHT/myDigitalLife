# DigitalLife
## DigitalLife - organize your digital life

> HTML with PocketBase 

###  Raspberry Pi Setup — execute once:

#### Download PocketBase  (ARM64 für Pi 4/5)
```
wget https://github.com/pocketbase/pocketbase/releases/latest/download/pocketbase_linux_arm64.zip
unzip pocketbase_linux_arm64.zip
``` 

### Start
```
./pocketbase serve --http="0.0.0.0:8090"
```
#### Create PocketBase Collection on http://pi-ip:8090/_/:

> → Collections → + New collection
Name: store
Feld 1: key — Plain text, Required
Feld 2: val — Plain text, Required
→ under API Rules: leave all rules blank (open for LAN)

#### In the App:

> click PB ⚙ Button → enter URL (z.B. http://192.168.1.50:8090) → Connect

#### As a systemd-daemon (in background) :
```
sudo nano /etc/systemd/system/pocketbase.service
```
> paste and save:
```
[Unit]
Description=PocketBase
After=network.target

[Service]
ExecStart=/home/pi/pocketbase/pocketbase serve --http="0.0.0.0:8090"
WorkingDirectory=/home/pi/pocketbase
Restart=always

[Install]
WantedBy=multi-user.target
```
#### Start and enable service:
```sudo systemctl enable --now pocketbase```

### Done
