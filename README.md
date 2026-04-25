# Práctica Final: Pipeline CI/CD con GitHub Actions, Docker y Render

Este proyecto consiste en una aplicación web básica "Hola Mundo" desarrollada en Python (Flask), diseñada para demostrar un flujo completo de **DevOps** utilizando herramientas de Integración Continua y Despliegue Continuo (CI/CD).

## 🚀 Tecnologías Utilizadas

* **Lenguaje:** Python 3.9
* **Framework Web:** Flask
* **Pruebas:** Unittest
* **Containerización:** Docker
* **CI/CD:** GitHub Actions
* **Registro de Imágenes:** Docker Hub
* **Hosting de Producción:** Render

## 🛠️ Estructura del Proyecto

* `app.py`: Aplicación web principal con un endpoint `/`.
* `test_app.py`: Pruebas unitarias para verificar el estado de la aplicación.
* `Dockerfile`: Instrucciones para empaquetar la aplicación en una imagen.
* `.github/workflows/main.yml`: Configuración del pipeline de automatización.

## ⚙️ Funcionamiento del Pipeline (CI/CD)

El pipeline se dispara automáticamente con cada `push` a la rama `main` y realiza los siguientes pasos:

1.  **Build & Test:**
    * Configura el entorno de Python.
    * Instala las dependencias necesarias (`requirements.txt`).
    * Ejecuta las **pruebas unitarias**. Si las pruebas fallan, el pipeline se detiene.

2.  **Build & Push Docker:**
    * Si las pruebas pasan, se construye una imagen de Docker.
    * La imagen se sube automáticamente a **Docker Hub**.

3.  **Deploy:**
    * Se envía una señal (WebHook) a **Render** para que descargue la nueva imagen de Docker Hub y actualice la aplicación en producción.

## 📦 Cómo ejecutar localmente

Si tienes Docker instalado, puedes ejecutar la aplicación con:

```bash
docker build -t hola-mundo-devops .
docker run -p 5000:5000 hola-mundo-devops
