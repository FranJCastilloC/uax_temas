# Matemáticas Studio

Biblioteca interactiva de matemáticas, estadística, programación y aprendizaje automático. Incluye explicaciones visuales, ejercicios, rutas de estudio, referencias bibliográficas y seguimiento del progreso.

## Ejecutar localmente

Necesitas Python 3. Desde la raíz del proyecto ejecuta

```sh
python3 -m http.server 8765 --bind 127.0.0.1 --directory biblioteca
```

Abre http://localhost:8765. El progreso se guarda en el almacenamiento local de tu navegador. Esta modalidad funciona sin credenciales, Redis ni instalación de paquetes.

## Configuración privada

.env.example contiene los nombres de las variables para Vercel. Cópialo como .env.local para usar vercel dev y completa tus credenciales. Para producción configura las variables en el panel de Vercel. Un archivo .env por sí solo requiere una herramienta que lo cargue.

```sh
cp .env.example .env.local
npm ci
npx vercel dev
```

BIBLIOTECA_USUARIO y BIBLIOTECA_CLAVE protegen las páginas y la API. UPSTASH_REDIS_REST_URL y UPSTASH_REDIS_REST_TOKEN conectan una base Redis propia. PREFIJO_REDIS identifica los datos de la instalación y VENTANA_FOTO_MIN controla el intervalo entre fotografías del progreso.

Los archivos .env y .env.local están excluidos de Git. Conserva las credenciales en tu equipo o en el proveedor de despliegue.

## Publicar tu instalación

Para Vercel sigue [VERCEL.md](VERCEL.md). Para Docker con Caddy y SQLite sigue [despliegue/LEEME.md](despliegue/LEEME.md).

La sincronización del servidor usa un espacio de progreso por instalación. Las personas con las credenciales de esa instalación comparten notas, progreso e historial.

## Estructura

- biblioteca/index.html muestra el catálogo y las rutas de estudio.
- biblioteca/conceptos/ contiene las páginas interactivas.
- biblioteca/catalogo.js registra los conceptos y sus relaciones.
- biblioteca/fuentes.js registra títulos, autores y notas bibliográficas.
- biblioteca/nucleo/ contiene los estilos, el motor compartido y los verificadores.
- api/index.py implementa la sincronización con Redis en Vercel.
- middleware.js controla el acceso en Vercel.
- despliegue/ contiene la alternativa Docker con SQLite.

Las citas conservan la fuente, sección y numeración de página para localizar la lectura en la edición correspondiente.

## Verificar cambios

Requiere Node.js y Python 3. Desde la raíz ejecuta

```sh
node --check biblioteca/nucleo/nucleo.js
python3 biblioteca/nucleo/verificar_catalogo.py
python3 biblioteca/nucleo/verificar.py biblioteca/conceptos/covarianza.html
```

## Crear un repositorio público

Para migrar desde una copia con historial privado, utiliza una exportación limpia de los archivos actuales y crea un repositorio nuevo. El historial anterior conserva versiones de los datos eliminados.

En la carpeta exportada ejecuta

```sh
git init -b main
git config user.name "Tu nombre público"
git config user.email "Tu correo noreply de GitHub"
git add .
git commit -m "Versión pública inicial"
```

Crea un repositorio vacío en tu cuenta de GitHub y sigue sus instrucciones para agregar el remoto y subir la rama main. Antes de subir revisa git diff --cached y git ls-files para comprobar qué archivos se incluyen.
