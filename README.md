# TP4_Litter_Sanabria_ojeda
/=====README=====/

Maze Bank - Billetera Virtual Descripción del proyecto

Este proyecto es una billetera virtual tipo sistema bancario desarrollado con Node.js, Express, MySQL, HTML, CSS y JavaScript. Permite el registro e inicio de sesión de usuarios, realización de transferencias entre cuentas, gestión de saldo y un panel de administración para control general del sistema.

Cómo levantar la aplicación Requisitos Node.js instalado MySQL instalado npm Instalación

Clonar el repositorio:

git clone cd BilleteraVirtual

Instalar dependencias:

npm install

Configuración de variables de entorno

Crear un archivo .env con el siguiente contenido:

DB_HOST=localhost DB_USER=root DB_PASS=tu_password DB_NAME=billetera_virtual JWT_SECRET=supersecretkey PORT=3000

Crear base de datos

Ejecutar en MySQL:

CREATE DATABASE billetera_virtual;

Luego importar las tablas necesarias:

usuarios transferencias Ejecutar el servidor

Modo normal:

npm start

Modo desarrollo:

npx nodemon server.js

Acceso a la aplicación

Frontend:

http://localhost:3000

Checklist de seguridad implementada

Autenticación con JWT
Se utiliza JSON Web Token para autenticar usuarios en rutas protegidas. Sin token válido no se puede acceder a funciones del sistema.

Middleware de protección de rutas
Se implementa verificación de token y verificación de rol para proteger rutas sensibles del sistema.

Sistema de roles (usuario / admin)
El sistema distingue entre usuarios normales y administradores, restringiendo el acceso a funciones críticas.

Validación de saldo en transferencias
El sistema valida que el usuario tenga saldo suficiente antes de realizar una transferencia.

Uso de transacciones SQL
Las transferencias se ejecutan dentro de transacciones para evitar inconsistencias en la base de datos.

Bloqueo de registros (FOR UPDATE)
Se bloquean filas durante la transferencia para evitar condiciones de carrera.

Rate limiting en login
Se limita la cantidad de intentos de inicio de sesión para prevenir ataques de fuerza bruta.

Rate limiting en transferencias
Se limita la cantidad de transferencias por segundo para evitar abuso del sistema.

Hash de contraseñas
Las contraseñas se almacenan en base de datos utilizando bcrypt, evitando almacenamiento en texto plano.

Validación de datos de entrada
Se valida email, monto y existencia de usuarios antes de ejecutar cualquier operación.

Auditoría de seguridad

Se utilizó Gitleaks para analizar el repositorio en busca de secretos expuestos.

Resultado del análisis:

No leaks found

Esto confirma que no hay credenciales, tokens ni secretos expuestos en el proyecto.
