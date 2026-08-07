# Sequel - HTB Starting Point

## Resumen
MySQL/MariaDB sin autenticación, flag en tabla dentro de la base de datos.

## Proceso
Nmap top 1000 no mostró nada. 
Escaneo completo (`-p-`) encuentra puerto 3306 (MySQL). 
Conexión pide SSL, se bypassea con `--skip-ssl`. 
Se entra como root sin password. 
Se listan las bases de datos disponibles, se navega hasta `htb`, donde la tabla `config` contiene la flag.

## Flag
<details>
<summary>Ver flag</summary>

`7b4bec00d1a39e3dd4e021ec3d915da8`

</details>
