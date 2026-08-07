# Appointment - HTB Starting Point

## Resumen
Máquina Very Easy que explota SQL Injection básica para hacer bypass de login.

## Reconocimiento
1. Nmap básico detecta puerto 80 TCP (HTTP)
2. Ingreso vía navegador a `http://IP_OBJETIVO`
3. Se encuentra un login básico, se deduce que el siguiente paso es SQL Injection

## Explotación
Con ayuda de IA aprendo métodos de SQL Injection básicos y su contraparte defensiva (prepared statements).

Payload usado en usuario y contraseña: ' or '1'='1

El login cede por SQL Injection, se encuentra la flag.

## Flag
<details>
<summary>Ver flag</summary>

`e3d0796d002a446c0e622226f42e9672`

</details>
