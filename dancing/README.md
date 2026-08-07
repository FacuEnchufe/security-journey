1- nmap no funciona, el mismo cmd dice probar con -Pn.
2- devuelve puertos 135, 139, 445 (firma de windows) (-> se intuye que la maquina es windows)
3- el puerto 445 SMB nos permite listar los archivos de la maquina y ver discos
4- De los 4 directorios solo podemos acceder WorkShares -> accedemos a los usuarios
 y bajamos la flag descargando toda la data de àmbos directamente.
