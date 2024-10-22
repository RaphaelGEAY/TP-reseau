#### Fait par Raphaël GEAY

# II. Serveur Web

## 🌞 Lister les ports en écoute sur la machine

```powershell
[raphael@Web ~]$ sudo ss -lnpt | grep nginx
```

```
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=11311,fd=6),("nginx",pid=11310,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=11311,fd=7),("nginx",pid=11310,fd=7))
```

##  🌞 Ouvrir le port dans le firewall de la machine

```powershell
[raphael@Web ~]$ sudo firewall-cmd --permanent --add-port=80/tcp
```

```
success
```

```powershell
[raphael@Web ~]$ sudo firewall-cmd --reload
```

```
success
```

## 🌞 Vérifier que ça a pris effet

```bash
raphael@Client1:~$ ping sitedefou.tp7.b1
```

```
PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=2.90 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=0.875 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=1.21 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=4 ttl=64 time=0.914 ms
^C
--- sitedefou.tp7.b1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 0.875/1.473/2.897/0.831 ms
```

```bash
raphael@Client1:~$ curl sitedefou.tp7.b1
```

```
meow !
```
