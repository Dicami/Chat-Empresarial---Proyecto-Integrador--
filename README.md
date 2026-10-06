# Connecta - Chat Empresarial Inter-Sedes

Sistema de comunicación interna y chat empresarial cliente-servidor desarrollado en **Go** e integrado con un servicio de autenticación en **FastAPI (Python)**. Esta solución permite la interacción segura, autenticada y trazable mediante mensajería directa y canales entre los colaboradores de la Sede A y Sede B.

---

## Descripción del Sistema

La solución responde a la problemática de la empresa tecnológica tras la apertura de su segunda sede operativa (Sede B). Anteriormente, la coordinación entre sedes se realizaba a través de canales informales y no autenticados, generando riesgos de fuga de información, falta de auditoría y problemas de trazabilidad.

Connecta centraliza la comunicación a través de:

- **Servidor de Chat (Go):** Gestiona la conexión de clientes mediante WebSockets, procesa rutas REST para el historial y canales, e implementa persistencia de mensajes y registros de sesión.
- **Servicio de Autenticación (FastAPI):** Gestiona la verificación de credenciales corporativas (contraseñas con hash `bcrypt`) y la emisión de tokens JWT.
- **Cliente de Consola (Go):** Interfaz CLI liviana que permite a los colaboradores enviar/recibir mensajes directos, unirse a canales y consultar historiales.

---

## Integrantes del Equipo

- Emilio Cuenca
- Danna Simaluisa
- Camila Villagran

---

## Alcance Preliminar

### Incluido en el Proyecto
- **Autenticación Segura:** Inicio de sesión con correo corporativo y contraseñas protegidas mediante hash `bcrypt`. Emisión de tokens JWT con roles (Usuario y Administrador).
- **Mensajería Básica:** Mensajes de texto directos (persona a persona) y mensajes en canales/grupos.
- **Historial de Mensajes:** Consulta de los últimos 50 mensajes por conversación.
- **Control de Sesiones:** Expiración automática de sesión a los 60 minutos, cierre manual y registro de *timestamps* de inicio/fin.
- **Administración y Configuración:** Creación de perfiles, gestión de permisos, creación de canales públicos/privados y auditoría de conversaciones.
- **Componente Estadístico:** Registro de eventos de uso (mensajes, sesiones, tiempos) y exportación de métricas a CSV.
- **Despliegue Distribuido:** Servidor Go y FastAPI en la Sede A, conectando a clientes ubicados tanto en la Sede A como en la Sede B a través de la red corporativa.

### Fuera del Alcance
- Envío de archivos, imágenes, audios o documentos (solo mensajes de texto)
- Llamadas de voz o video
- Interfaz gráfica (GUI), aplicaciones móviles o web (el cliente es de consola)
- Cifrado de extremo a extremo (E2EE); la protección se basa en contraseñas con hash y tokens JWT
- Edición o eliminación de mensajes enviados
- Alta disponibilidad, balanceo de carga y despliegue en la nube (excluidos por el documento del Proyecto Integrador, sección 2.4)

---

## Estructura del Repositorio

```text
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
