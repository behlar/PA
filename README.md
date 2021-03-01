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
	sudo sed -i '/TURNSERVER_ENABLED/c\TURNSERVER_ENABLED=1' /etc/default/coturn
#### Konfiguration des Coturn-Servers erzeugen
#### Ersetzen Sie in der nachfolgenden Konfiguration <Schlüssel 1> mit dem oben erzeugten Schlüssel.
	vim /etc/turnserver.conf
#### Folgenden Inhalt in die Datei einfügen, <Schlüssel 1> und <Schlüssel 6> durch die oben erzeugten Schlüssel ersetzen und die Domäne (realm=) anpassen:
	listening-port=3478
	fingerprint
	use-auth-secret
	static-auth-secret=<Schlüssell 1>
	realm=
	total-quota=0
	bps-capacity=0
	no-tls
	no-dtls
	stale-nonce
	no-stdout-log
	log-file=/tmp/coturn.log
	no-multicast-peers
