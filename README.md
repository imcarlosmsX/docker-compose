# 🐳 Proyecto Multi-contenedor con Docker Compose

## 📄 Descripción del Proyecto

Este proyecto tiene como objetivo configurar un entorno multi-contenedor utilizando Docker Compose, en el cual se despliegan tres servicios web. Cada uno de estos servicios se ejecuta en su propio contenedor:

1. **Proxy (Nginx o Caddy)**: Funciona como proxy reverso, manejando las solicitudes HTTP en el puerto 80.
2. **Aplicación Web 1**: Basada en un repositorio de [proyectos de Ingeniería Uninorte](https://github.com/proyectosingenieriauninorte), expone el servicio en el puerto 8000.
3. **Aplicación Web 2**: Otra instancia de una aplicación web del mismo repositorio, expuesta en el puerto 8001.

El proxy se encarga de redirigir las solicitudes a `/c2` hacia la Aplicación Web 1 y a `/c3` hacia la Aplicación Web 2.

## 📂 Estructura del Proyecto

```bash
docker-compose-proyecto/
│
├── docker-compose.yml          # Configuración de Docker Compose
├── nginx.conf                  # Archivo de configuración del proxy Nginx
├── index.html                  # Página de bienvenida principal
├── app1/                       # Directorio para la Aplicación Web 1
│   ├── Dockerfile              # Dockerfile para construir la imagen de app1
│   ├── index.html              # Página principal de la aplicación
│   └── ...                     # Otros archivos de la aplicación web 1
└── app2/                       # Directorio para la Aplicación Web 2
    ├── Dockerfile              # Dockerfile para construir la imagen de app2
    ├── index.html              # Página principal de la aplicación
    └── ...                     # Otros archivos de la aplicación web 2
```

## 🚀 Instrucciones para Ejecutar el Proyecto

### 1️⃣ Configuración Previa

1. **Clonar el Repositorio**: Descarga el proyecto a tu máquina local.

   ```bash
   git clone https://github.com/imcarlosmsX/docker-compose.git
   cd docker-compose
   ```

2. **Verificar Instalación de Docker Compose**: Asegúrate de que Docker y Docker Compose están instalados.

   ```bash
   docker-compose --version
   ```

### 2️⃣ Compilación y Ejecución

1. **Construir y Desplegar los Contenedores**: Dentro del directorio del proyecto, ejecuta:

   ```bash
   docker-compose up --build
   ```

   Este comando construye las imágenes necesarias y lanza los tres contenedores.

### 3️⃣ Acceso a los Servicios

1. **Página de Bienvenida**: Para visualizar la página de bienvenida del proxy, visita:

   - [http://localhost](http://localhost)

2. **Navegar a las Aplicaciones Web**:

   - [Aplicación Web 1](http://localhost/c2)
   - [Aplicación Web 2](http://localhost/c3)

## 🔧 Detalles Técnicos

- **Proxy Nginx**: Configurado para redirigir el tráfico basado en las rutas `/c2` y `/c3`.
- **Dockerfiles**: Cada aplicación cuenta con su propio `Dockerfile` dentro de sus respectivos directorios `app1` y `app2`, permitiendo personalizar el entorno de ejecución de cada contenedor.
- **Red de Docker**: Los contenedores se encuentran en la misma red definida en `docker-compose.yml`, facilitando la comunicación entre ellos.