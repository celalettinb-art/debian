# debian
Consume und Export Ordner liegen unter /data/compose/x/ (oder /var/lib/docker/volumes/paperless_data/_data)
Samba installieren und konfigurieren
	apt install samba smbclient
	nano /etc/samba/smb.conf
		[paperless-consume]
		path = /data/compose/2/
		browseable = yes
		writable = yes
		guest ok = no
		valid users = cello
	Benutzer für Samba anlegen:
		smbpasswd -a cello
	Berechtigungen an dem Ordner anpassen
		chown cello:cello /data/compose/2/
		chmod 775 /data/compose/2/
	Den Samba Dienst neu starten
		systemctl restart smbd
	Samba User auflisten
		pdbedit -w -L

##### Sonstiges #####
systemctl --type=service --state=running list-units

Keyboard ändern
apt update
apt install keyboard-configuration
dpkg-reconfigure keyboard-configuration
apt install kbd console-setup

Docker
docker ps --format "table {{.Names}}\t{{.Ports}}"
