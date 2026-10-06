# Connecta - Chat Empresarial Inter-Sedes

Sistema de comunicación interna y chat empresarial cliente-servidor desarrollado en **Go** e integrado con un servicio de autenticación en **FastAPI (Python)**. Esta solución permite la interacción segura, autenticada y trazable mediante mensajería directa y canales entre los colaboradores de la Sede A y Sede B.

---

##  Descripción del Sistema

La solución responde a la problemática de la empresa tecnológica tras la apertura de su segunda sede operativa (Sede B)[cite: 1]. Anteriormente, la coordinación entre sedes se realizaba a través de canales informales y no autenticados, generando riesgos de fuga de información, falta de auditoría y problemas de trazabilidad[cite: 1].

**Connecta** centraliza la comunicación a través de:
* **Servidor de Chat (Go):** Gestiona la conexión de clientes  mediante WebSockets, procesa rutas REST para el historial y canales, e implementa persistencia de mensajes y registros de sesión[cite: 1].
* **Servicio de Autenticación (FastAPI):** Gestiona la verificación de credenciales corporativas (contraseñas con hash `bcrypt`) y la emisión de tokens JWT[cite: 1].
* **Cliente de Consola (Go):** Interfaz CLI liviana que permite a los colaboradores enviar/recibir mensajes directos, unirse a canales y consultar historiales[cite: 1].

---

##  Integrantes del Equipo

* **Emilio Cuenca**
* **Danna Simaluisa**
* **Camila Villagran**


---

##  Alcance Preliminar

### Incluido en el Proyecto
* **Autenticación Segura:** Inicio de sesión con correo corporativo y contraseñas protegidas mediante hash `bcrypt`. Emisión de tokens JWT con roles (`Usuario` y `Administrador`)[cite: 1].
* **Mensajería Básica:** Mensajes de texto directos (persona a persona) y mensajes en canales/grupos[cite: 1].
* **Historial de Mensajes:** Consulta de los últimos 50 mensajes por conversación[cite: 1].
* **Control de Sesiones:** Expiración automática de sesión a los 60 minutos, cierre manual y registro de timestamps de inicio/fin[cite: 1].
* **Administración y Configuración:** Creación de perfiles, gestión de permisos, creación de canales públicos/privados y auditoría de conversaciones[cite: 1].
* **Componente Estadístico:** Registro de eventos de uso (mensajes, sesiones, tiempos) y exportación de métricas a CSV[cite: 1].
* **Despliegue Distribuido:** Servidor Go y FastAPI en la Sede A, conectando a clientes ubicados tanto en la Sede A como en la Sede B a través de la red corporativa[cite: 1].

### Fuera del Alcance
* Envío de archivos multimedia (imágenes, audios, documentos)[cite: 1].
* Llamadas de voz o video[cite: 1].
* Interfaz gráfica de usuario (GUI) o aplicaciones móviles/web[cite: 1].
* Cifrado de extremo a extremo (E2EE)[cite: 1].
* Edición o eliminación de mensajes enviados[cite: 1].
* Balanceo de carga y alta disponibilidad en la nube[cite: 1].

---

##  Estructura del Repositorio

Chat-empresarial/
├── app-go/                  # Cliente y Servidor en Go
├── auth-service/            # Servicio de autenticación en FastAPI (Python)
├── network/                 # Configuración de red y reglas de comunicación inter-sedes
├── research/                # Investigaciones y análisis previos
├── docs/                    # Documentación del proyecto
│   └── especificacion-requisitos.pdf  # Análisis, especificación de requisitos, casos de uso, matriz y guion
├── tests/                   # Pruebas de integración y validación
├── docker-compose.yml       # Orquestación de contenedores (Servidor Go, FastAPI, BD)
├── .gitignore
├── LICENSE
└── README.md
