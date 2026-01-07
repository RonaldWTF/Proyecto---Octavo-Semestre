==============================================================================
   GUÍA DE INSTALACIÓN DEL BACKEND (SERVIDOR Y BASE DE DATOS)
   Tecnología: Docker + Microservicios
==============================================================================

Hola equipo,
Estos son los pasos para levantar el "cerebro" del proyecto (Base de datos y APIs)
en sus computadoras usando Docker. Sigan los pasos en orden.

------------------------------------------------------------------------------
PARTE 1: INSTALACIÓN DE DOCKER (OBLIGATORIO)
------------------------------------------------------------------------------
Como estamos usando contenedores, no necesitan instalar MongoDB ni Node.js
para la base de datos, pero SÍ necesitan instalar Docker Desktop.

1. HABILITAR WSL 2 (Motor de Linux para Windows)
   a. Abran PowerShell como Administrador (Click derecho en Inicio > Terminal Admin).
   b. Escriban el siguiente comando y den Enter:
      
      wsl --install

   c. Si les pide reiniciar la computadora, REINICIEN AHORA MISMO.
   d. Si dice que ya está instalado, continúen al paso 2.

2. INSTALAR DOCKER DESKTOP
   a. Descarguen el instalador aquí: 
      https://www.docker.com/products/docker-desktop/
   b. Ejecuten el instalador.
   c. IMPORTANTE: Marquen la casilla que dice "Use WSL 2 instead of Hyper-V".
   d. Al finalizar, abran la aplicación "Docker Desktop" desde el menú inicio.
   e. Acepten los términos.
   f. Esperen a que la franja inferior izquierda de la ventana diga en verde: 
      "ENGINE RUNNING". (Esto puede tardar unos minutos).

3. VERIFICAR INSTALACIÓN
   Abran una terminal (PowerShell o CMD) y escriban:
   
   docker --version

   Si sale un número de versión, ya están listos.

------------------------------------------------------------------------------
PARTE 2: LEVANTAR LOS SERVIDORES
------------------------------------------------------------------------------
1. Abran VS Code en la carpeta raíz del proyecto ("nicholog-microservices").
   Asegúrense de ver el archivo 'docker-compose.yml'.

2. Abran una terminal en VS Code y ejecuten este comando:

   docker compose up --build

   (Nota: Si les da error, prueben con guion: "docker-compose up --build").

3. ESPEREN CON PACIENCIA ☕
   La primera vez tardará entre 5 y 10 minutos porque descargará las imágenes
   de Node.js y MongoDB de internet.

4. ¿CÓMO SABER SI YA TERMINÓ?
   La terminal NO les devolverá el control. Se quedará "trabada" mostrando logs.
   Esto es normal.
   Busquen mensajes como:
   - "GATEWAY corriendo en http://localhost:8080"
   - "MongoDB Conectado"
   - "WiredTiger message" (Logs de la base de datos).

   --> NO CIERREN ESTA TERMINAL. Si la cierran, se apaga el servidor.

------------------------------------------------------------------------------
PARTE 3: ACTIVAR DATOS DE PRUEBA (SEED)
------------------------------------------------------------------------------
Para verificar que todo funciona y crear los usuarios por defecto en la Base de Datos:

1. Sin cerrar la terminal, abran su navegador (Chrome/Edge).
2. Entren a este enlace:

   http://localhost:5002/seed

3. Deberían ver un mensaje en formato JSON (texto negro/verde) que dice:
   "message": "✅ Base de datos reiniciada y poblada con éxito..."

¡LISTO! 🚀
Si ven ese mensaje, su Backend de Microservicios está funcionando al 100%.

------------------------------------------------------------------------------
SOLUCIÓN DE ERRORES COMUNES
------------------------------------------------------------------------------
* Error: "docker no se reconoce como un nombre de cmdlet..."
  -> Significa que no instalaste Docker Desktop o no reiniciaste la PC.

* Error: "Set-ExecutionPolicy..." o permisos denegados en PowerShell.
  -> Ejecuta este comando en la terminal para dar permisos:
     Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass

* Error: El comando se queda pegado y no hace nada.
  -> Revisa que la aplicación Docker Desktop esté abierta y con la luz verde.

==============================================================================