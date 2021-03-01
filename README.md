#### Installation der Firewall:
	apt install ufw -y

#### Konfiguration und Aktivierung der Firewall:
	ufw allow http
	ufw allow https
	ufw allow ssh
	ufw allow 3478/tcp
	ufw allow 3478/udp
	ufw enable

