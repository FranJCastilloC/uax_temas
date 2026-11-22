# Biblioteca con Docker

Requiere Docker con Compose. Ejecuta los comandos desde despliegue/.

1. Copia .env.ejemplo a .env.
2. Completa USUARIO y CLAVE_HASH. Genera el hash con docker run --rm -it caddy:2.8.4-alpine caddy hash-password. En el archivo .env escapa cada signo dólar del hash como $$.
3. Para probar localmente configura DOMINIO=:80 y PUERTO_HTTP=8080.
4. Ejecuta docker compose up -d --build y abre http://localhost:8080.
5. Para detener ejecuta docker compose down.

Para HTTPS público configura DOMINIO con tu dominio, apunta el DNS al servidor y permite los puertos 80 y 443. Configura VPS y CARPETA_VPS para usar desplegar.sh desde la raíz del proyecto.

SQLite guarda el progreso en datos/progreso.db. Respaldar.sh copia la base desde el VPS a respaldos/. Estas carpetas y el .env están excluidos de Git. El progreso se comparte entre las personas que usan las credenciales de esta instalación.

Las fuentes son referencias bibliográficas. La imagen web sirve biblioteca/ y la API de progreso.
