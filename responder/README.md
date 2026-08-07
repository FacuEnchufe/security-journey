# Responder - HTB Starting Point

## Resumen
Máquina Windows. Explota LFI/RFI en un parámetro de idioma web para forzar captura de hash NTLM, se crackea la password y se obtiene shell remota vía WinRM.

## Proceso
Nmap detecta puertos 80 (HTTP) y 5985 (WinRM). La web usa un dominio custom (`unika.htb`), agregado manualmente a `/etc/hosts` para poder accederla. El parámetro `page=` de la URL (usado normalmente para cambiar idioma) resulta vulnerable a File Inclusion — no valida qué archivo/recurso carga.

Se explota como RFI apuntando el parámetro a la propia IP del atacante, mientras `Responder` escucha en la interfaz de red. El servidor Windows, al intentar acceder a ese "recurso remoto", inicia automáticamente su proceso de autenticación NTLM, revelando su hash (NetNTLMv2) a Responder.

El hash capturado se crackea con `John The Ripper` contra el diccionario rockyou.txt, obteniendo la password en texto plano del usuario Administrator. Con esas credenciales, se establece conexión remota vía `Evil-WinRM` (puerto 5985), obteniendo shell completa en la máquina para navegar hasta encontrar la flag.

## Flag
<details>
<summary>Ver flag</summary>

`ea81b7afddd03efaa0945333ed147fac`

</details>
