## Desafío: Configuración de GitHub Actions para despliegues en EC2

### Introducción

Este repositorio contiene el flujo de trabajo de GitHub Actions configurado para automatizar el despliegue de una aplicación web en una instancia de Amazon EC2. Este proceso simplifica el ciclo de vida del desarrollo y garantiza que los cambios se reflejen rápidamente en la producción.


### Requisitos Previos
* **Cuenta de AWS:** Con credenciales configuradas en los secretos de GitHub.
* **Repositorio de GitHub:** Contiene el código de la aplicación.
* **Clave SSH:** Para acceder a la instancia EC2.

### Configuración
1. **Secretos de GitHub:**
   * **AWS_ACCESS_KEY_ID:** Clave de acceso de AWS.
   * **AWS_SECRET_ACCESS_KEY:** Clave secreta de AWS.
   * **PASSWORD_SERVER:** Contraseña del usuario en la instancia EC2.
   * **USER_SERVER:** Nombre de usuario en la instancia EC2.

2. **docker-compose.yml:**
   * Configura los servicios de tu aplicación (ej: web, base de datos).

### Flujo de Trabajo
1. **Trigger:** El flujo se activa al realizar un push a la rama `main`.
2. **Creación de la instancia:** Si no existe, se crea una instancia EC2 con las especificaciones definidas.
3. **Clonación del repositorio:** Se clona el repositorio en la instancia.
4. **Instalación de dependencias:** Se instalan las dependencias necesarias (Node.js, Python, etc.).
5. **Copiar archivos:** Se copian los archivos del proyecto local a la instancia.
6. **Iniciar la aplicación:** Se utiliza `docker-compose up -d` para iniciar los servicios.

