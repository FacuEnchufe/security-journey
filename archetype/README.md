# Archetype - HTB Starting Point

## Resumen
Máquina Windows. MSSQL mal configurado permite ejecución de comandos, escalando desde acceso de servicio hasta Administrator vía credenciales expuestas en historial de PowerShell.

## Proceso
Nmap detecta puertos típicos de Windows (135, 139, 445) más MSSQL (1433) y WinRM (5985). El share SMB `backups` permite acceso anónimo y contiene un archivo de configuración (`prod.dtsConfig`) con credenciales en texto plano del usuario `sql_svc`.

Con esas credenciales se conecta a MSSQL vía `impacket-mssqlclient`. Se habilita `xp_cmdshell`, permitiendo ejecución de comandos del sistema operativo directamente desde SQL. Se monta un servidor HTTP local para servir un script de reverse shell en PowerShell, y se dispara su descarga y ejecución vía `xp_cmdshell`, obteniendo shell interactiva como `sql_svc` a través de un listener de Netcat.

Con acceso de shell, se sube `WinPeas` (mismo método de servidor HTTP) para enumerar vectores de escalación de privilegios. WinPeas señala el archivo de historial de PowerShell (`ConsoleHost_history.txt`), que contiene la contraseña del usuario `administrator` en texto plano (dejada ahí por un comando previo del propio admin conectándose al share de backups).

Con esas credenciales, se establece conexión limpia vía `Evil-WinRM`, obteniendo acceso completo como Administrator.

## Flags
<details>
<summary>Ver flags</summary>

User: `3e7b102e78218e935bf3f4951fec21a3`

Root/Admin: `b91ccec3305e98240082d4474b848528`

</details> 
