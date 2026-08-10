Three — HackTheBox (Starting Point)

Resumen: Linux muy fácil. Bucket S3 mal configurado, usado como backend de un sitio web. Acceso vía AWS CLI sin credenciales reales, escritura habilitada, web shell PHP subida al bucket → reverse shell.

Proceso
nmap: 22 (descartado) y 80 (Apache, título "The Toppers").
gobuster dir sobre la IP: sin resultados útiles.
Título no coincide con el nombre de la máquina → hipótesis de vhost por nombre visible en la página.
Fuzzing de subdominios (wordlist genérica): sin resultados, wordlist no temática.
Subdominio real (s3.*) confirmado por el panel de la máquina, no por fuzzing.
Headers de la respuesta → LocalStack (emulador de S3), métodos de escritura habilitados.
AWS CLI, credenciales falsas + --endpoint-url → acceso al bucket sin auth real.
Bucket = backend real del sitio (mismos archivos que el sitio web).
Escritura confirmada con archivo de prueba.
Web shell PHP subida al bucket, listener netcat en espera, visita a la URL dispara ejecución → reverse shell.
Post-explotación estándar hasta la flag.

