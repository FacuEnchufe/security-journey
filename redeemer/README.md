1- Hacemos nmap "simple", no detecta ni un puerto TCP.
2- para descartar ahora hago un nmap para UDP, detecta 1 pero es humo.
3- vuelvo a hacer un nmap TCP completo, detecta el puerto 6379 Redis abierto.
4- conectamos mediante redis-cli -h 
5- dentro de la bd reviso todo el contenido con keys *
6- extraigo la flag con get.
