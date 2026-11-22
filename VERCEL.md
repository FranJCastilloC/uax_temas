# Despliegue en Vercel

Importa tu copia del repositorio en Vercel. El archivo vercel.json configura la salida estática biblioteca/, el middleware y las funciones Python de api/.

En Settings → Environment Variables configura BIBLIOTECA_USUARIO y BIBLIOTECA_CLAVE con valores propios. El middleware protege las páginas y la API. Si faltan estas variables devuelve HTTP 503.

Crea una base Upstash Redis propia y configura UPSTASH_REDIS_REST_URL y UPSTASH_REDIS_REST_TOKEN. También se aceptan KV_REST_API_URL y KV_REST_API_TOKEN. PREFIJO_REDIS permite elegir el prefijo de las claves. Cada instalación debe usar su propia base o prefijo.

Publica los cambios desde la rama conectada a tu proyecto. Tras cambiar variables de entorno, realiza un nuevo despliegue.

El progreso y las notas se sincronizan en un único espacio por instalación. Quienes compartan las credenciales comparten esos datos. Usa una instalación personal para guardar progreso privado.

Para desarrollo con la API, instala las dependencias con npm ci, copia .env.example a .env.local, completa los valores y ejecuta npx vercel dev. La vista estática descrita en README.md funciona sin Redis.
