# DesarrolloDeAplicacionesI
Sistema de Soporte e Incidencias (Help Desk) para la Optimización y Control de Ventas en Campo

Parte A: La Rama Descendente (Fase de Verificación)
La fase descendente comprende la traducción de las necesidades del negocio en especificaciones cada vez más detalladas y listas para su implementación técnica.
1. Análisis de Requisitos (Requirement Gathering)
Objetivo: Capturar, documentar y priorizar las necesidades de los usuarios finales y los objetivos de la distribuidora mayorista.
Actividades Clave:
	Levantamiento de casos de uso del personal de campo y de coordinación administrativa.
	Definición de requisitos funcionales (generación de tickets, categorización, asignación de prioridades) y no funcionales (tiempos de respuesta de base de datos, accesibilidad móvil offline/síncrona).
Entregables: Especificación de Requisitos de Software (SRS) y backlog priorizado de la aplicación.
2. Análisis del Sistema
Objetivo: Traducir los requisitos en un comportamiento general del software y definir su arquitectura funcional.
Actividades Clave:
	Definición del flujo de navegación de las interfaces.
	Elaboración de diagramas de secuencia e interacciones de usuario (workflows de resolución de incidencias).
	Establecimiento del modelo de negocio, reglas de transición de estados de un ticket (Ej: Nuevo > En Proceso > Resuelto).
Entregables: Casos de uso detallados, diagramas de flujo y arquitectura lógica del sistema.
3. Diseño de Software / Arquitectura (Software Design)
Objetivo: Estructurar los componentes principales, interfaces y tecnologías del ecosistema tecnológico.
Actividades Clave:
	Establecer el patrón de arquitectura MVC (Modelo-Vista-Controlador).
	Configurar la integración de componentes entre el Frontend (Vite.js) y el Backend (Django REST Framework).
	Diseño del flujo de red y almacenamiento en contenedores (Docker).
Entregables: Diagrama de arquitectura del sistema y contrato de APIs/Servicios.
4. Diseño de Módulos (Module Design)
Objetivo: Poner en detalle la lógica interna, algoritmos y el modelo de datos de cada componente.
Actividades Clave:
	Diseño de las clases, controladores y endpoints específicos (Autenticación, Gestión de Tickets, Logs de cambios).
	Modelado de datos en base de datos relacional (entidades para usuarios, roles, tickets, bitácoras e historial).
	Especificación de funciones y algoritmos de notificación o filtrado de prioridad.
Entregables: Diagramas de clases, esquema físico de base de datos y especificación técnica por componente.


5. Punto de Inflexión (El Vértice de Transición)
Definición: Es el hito metodológico que marca el final exacto de la rama descendente (planificación y diseño). Representa el vértice inferior del Modelo en V.
Objetivo: Actuar como una compuerta de validación. En este punto, los requisitos y diseños (arquitectura, base de datos, módulos) se congelan para ser traducidos a la realidad.
Condición de cruce: Para atravesar este punto de inflexión, el equipo debe garantizar que el entorno de trabajo está preparado (Docker configurado, repositorio de GitHub inicializado y stack de Python/Vite.js instalado).
6. Codificación (Fase de Implementación)
Definición: Es la fase de ejecución activa donde los desarrolladores escriben el código fuente del sistema basándose estrictamente en los planos aprobados en las fases anteriores.
Objetivo: Construir el software funcional que alimentará posteriormente la rama ascendente (fase de pruebas y verificación).
Actividades Clave (Stack Python/Django + Vite.js):
	Creación y configuración del proyecto backend estructurado en Django.
	Desarrollo del módulo de autenticación (registro, inicio de sesión y gestión de roles).
	Configuración del panel de administración (Django Admin) para la gestión de las tablas de base de datos.
	Construcción e integración de las vistas y plantillas que se mostrarán a los usuarios según sus privilegios (Administrador, Gestor, Usuario, Visitante).
Parte B: Condiciones Previas a la Codificación
Antes de escribir la primera línea de código de negocio, se debe cumplir obligatoriamente con el siguiente checklist técnico para garantizar la calidad, portabilidad y orden en el proyecto.
B.1- Stack de Desarrollo Instalado
Descargar e instalar en los equipos de desarrollo los componentes principales:
•	Python 3.11+
•	Docker & Docker Desktop
•	Node.js & npm (Para Vite.js)
B.2- Entorno Virtual con Docker
Para asegurar que todo el equipo trabaja sobre el mismo sistema y evitar fallos por "en mi máquina funciona":
•	Crear los archivos Dockerfile y docker-compose.yml.
•	Configurar un contenedor para el backend (Python/Django) y uno para el frontend (Vite.js), además del servicio de base de datos (PostgreSQL/MySQL).
B.3- Inicialización del Repositorio en GitHub
Implementación del sistema de control de versiones:
•	Crear el repositorio en GitHub con un archivo .gitignore adecuado para Python, Node y Docker.
•	Configurar la rama principal main o develop y establecer políticas de ramas (feature/, bugfix/).
B.4- Instalación de Django y Librerías Requeridas
•	Instalar e incluir las dependencias en el archivo requirements.txt del contenedor.
•	Librerías esenciales: django, djangorestframework, django-cors-headers, psycopg2-binary (para bases de datos relacionales).
B.5- Creación del Backend Django
•	Inicializar el proyecto base (django-admin startproject core . o backend).
•	Estructurar el directorio de forma modular (separando configuraciones, apps y utilidades).
B.6- Creación del Módulo de Registro e Inicio de Sesión
•	Implementar o utilizar la biblioteca integrada de usuarios de Django (AbstractUser).
•	Crear la app de Django para autenticación y login (startapp authentication o users), que maneje registros, validación de contraseñas y sesiones/tokens (JWT o sesión estándar).
B.7- Configuración del Django Admin
•	Registrar los modelos principales en admin.py (ej. Usuario, Ticket, Historial).
•	Personalizar la interfaz del administrador de Django para permitir la búsqueda, filtrado y edición rápida de datos de prueba durante las fases iniciales.
B.8- Configuración de Vistas Básicas y Plantillas según Roles
Estructurar las plantillas (templates) o rutas según los privilegios del sistema:
•	Administrador: Acceso total a dashboards, reasignaciones e historial global.
•	Gestor / Coordinador: Visualización de colas de tickets asignadas, filtros de prioridad y herramientas de resolución.
•	Usuario / Vendedor: Creación de nuevas incidencias y bandeja de progreso personal.
•	Visitante / No Autenticado: Vista de error de permisos o redirección a la pantalla de login.
