# 🐳 Flask + Docker + Pre-commits + Test
Proyecto en **Flask** contenerizado con **Docker**, incluyendo entorno de desarrollo, ejecución en producción, formateo automático con **Black**, test con **Pytest** y **hooks pre-commit** para mantener el código limpio antes de cada commit.

---

## 🚀 Ejecución en modo producción
Construir y ejecutar el contenedor con la aplicación Flask:
```bash
docker build -t mi-app:1.0 .
docker run -rm -p 8000:8000 mi-app:1.0
```
- Crea una imagen Docker a partir del Dockerfile.
- Ejecuta la imagen en un contenedor, mapeando el puerto 8000 del host al del contenedor y eliminando el contenedor al salir.

---

### 🧱 .dockerignore
```bash
.dockerignore
```
Evita que los archivos innecesarios se copien a la imagen Docker, reduciendo tamaño y mejorando tiempos de construcción.

---

## 💻 Entorno de desarrollo
Construir la imagen de desarrollo:
```bash
docker compose build dev
```
Comprobar la versión de Python dentro del contenedor:
```bash
docker compose run --rm -T dev python --version
```
## 🧪 Test con Pytest
Ejecutar los test dentro del contenedor:
```bash
docker compose run --rm -T dev pytest
```
Autoformatear los archivos is hay problemas:
```bash
docker compose run --rm -T dev black .
```

---

## 🪝 Hook pre-commit
El archivo se ejecuta **automáticamente antes de cada commit** y hace lo siguiente:
1. Ejecuta black . dentro del contenedor para formatear el código. Si el formato es incorrecto, bloquea el commit.
2. Ejecuta los test con pytest. Si algún test falla, también bloquea el commit.

---

Creado por 💻**Cristina**.

