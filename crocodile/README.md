# [Crocodile] - HTB Starting Point

## Resumen
FTP con credenciales expuestas + enumeración web para acceder a dashboard.

## Proceso
Nmap encuentra puertos 21 (FTP) y 80 (HTTP). 
FTP permite acceso anónimo y contiene dos archivos: una lista de usuarios y otra de passwords correspondientes por posición. 
La web principal no muestra login visible, así que se usa `gobuster` para enumerar rutas ocultas, encontrando `/dashboard/`. Se prueban las credenciales del FTP ahí, la primera combinación funciona y se obtiene acceso al panel, donde se encuentra la flag.

## Flag
<details>
<summary>Ver flag</summary>

`c7110277ac44d78b6a9fff2232434d16`

</details>
