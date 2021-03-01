#### Installation der Firewall:
	apt install ufw -y

#### Konfiguration und Aktivierung der Firewall:
	ufw allow http
	ufw allow https
	ufw allow ssh
	ufw allow 3478/tcp
	ufw allow 3478/udp
	ufw enable
#### Generierung von Schlüsseln (für später speichern!)
#### TURN-Key (Schlüssel 1)
	openssl rand -hex 32
#### API-Key (Schlüssel 2)
	openssl rand -base64 16
#### Nextcloud Secret-Key (Schlüssel 3)
	openssl rand -hex 16
#### Block-Key (Schlüssel 4)
	openssl rand -hex 16
#### Hash-Key (Schlüssel 5)
	openssl rand -hex 16
#### Coturn
	apt install coturn -y
	mv /etc/turnserver.conf /etc/turnserver.conf.bak
#### Coturn-Dienst aktivieren
	vim /etc/default/coturn
#### Kommentar-Zeichen entfernen:
	TURNSERVER_ENABLED=1
