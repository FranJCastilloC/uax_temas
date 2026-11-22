# UAX temas

Biblioteca local de matemáticas, estadística, programación y aprendizaje automático. Incluye explicaciones visuales, ejercicios, rutas de estudio y referencias bibliográficas.

## Ejecutar en tu computadora

Necesitas Python 3. Desde la carpeta del proyecto ejecuta

```sh
python3 -m http.server 8765 --bind 127.0.0.1 --directory biblioteca
```

Abre http://127.0.0.1:8765. Para detener el servidor pulsa Ctrl+C en la terminal.

El servidor escucha exclusivamente en tu computadora y sirve la carpeta biblioteca/. Usa siempre esa dirección y ese puerto para acceder al mismo progreso.

## Progreso y privacidad

El progreso, las respuestas y las notas se guardan en localStorage del navegador. Usa el mismo navegador y perfil para conservarlos. Borrar los datos del sitio o usar navegación privada puede eliminar ese progreso.

Las páginas cargan fuentes tipográficas de Google Fonts y KaTeX desde cdnjs para mostrar las fórmulas. Esas solicitudes requieren conexión a Internet y comunican tu dirección IP a esos proveedores. El código de la aplicación guarda las notas y el progreso en el navegador.

Las citas contienen títulos, autores, secciones y números de página para localizar la lectura en la edición correspondiente.

## Estructura

- biblioteca/index.html contiene la portada, el catálogo y las rutas de estudio.
- biblioteca/conceptos/ contiene las páginas interactivas.
- biblioteca/catalogo.js registra los conceptos y sus relaciones.
- biblioteca/fuentes.js registra las referencias bibliográficas.
- biblioteca/nucleo/ contiene el motor compartido, los estilos y los verificadores.

## Verificar cambios

Para las comprobaciones de desarrollo necesitas Node.js y Python 3. Ejecuta desde la raíz

```sh
node --check biblioteca/nucleo/nucleo.js
python3 biblioteca/nucleo/verificar_catalogo.py
python3 biblioteca/nucleo/verificar.py biblioteca/conceptos/covarianza.html
```

Antes de publicar cambios revisa los archivos preparados con git diff --cached. Los archivos de entorno y la configuración privada se excluyen mediante .gitignore.
