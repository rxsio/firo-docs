---
title: 3D Printer Network Setup
---

1. Edit `/etc/wpa_supplicant/wpa_supplicant.conf` file  
   Replace hotspot_ssid, hotspot_password, eduroam_login and eduroam_password accordingly. Eduroam configuration may vary by university.
```ini
ctrl_interface=/var/run/wpa_supplicant
update_config=1
country=DE

network={
	ssid="hotspot_ssid"
	psk="hotspot_password"
	priority=1
}

network={
	ssid="eduroam"
	key_mgmt=WPA-EAP
	eap=PEAP
	identity="eduroam_login"
	password="eduroam_password"
	phase2="auth=MSCHAPV2"
	priority=2
}          
```
2. Test your connectivity. Sometimes changing the configuration above may be sufficient. If the printer still does not connect to the hotspot or eduroam, then the following steps may help.
3. Remove or comment out all lines in `/etc/dnsmasq.conf`
4. In `/etc/default/hostapd` replace `DAEMON_CONF="/etc/hostapd/hostapd.conf"` with `DAEMON_CONF=""`
5. In `/etc/sysctl.conf` remove (or comment out) the line containing `net.ipv4.ip_forward=1`