# 🔍 Plataforma de Localización de Pacientes — Sismo Venezuela 2026

Plataforma digital de contingencia civil orientada a la unificación, búsqueda y localización en tiempo real de ciudadanos ingresados en los centros hospitalarios a raíz del evento sísmico del año 2026. 

Este sistema ha sido desplegado de forma anónima por la **Brigada Digital 2026** como una herramienta de interés público, acceso gratuito y código abierto para facilitar el reencuentro familiar de manera descentralizada, rápida y accesible desde dispositivos móviles o conexiones de red limitadas.

---

## 🔒 Arquitectura de Seguridad y Privacidad Operacional

Ante la sensibilidad en el manejo de datos de identidad en escenarios de crisis, esta plataforma fue diseñada bajo estrictos principios de seguridad digital:

1. **Estructura Serverless (Sin Base de Datos Externa):** Toda la lógica corre directamente en el dispositivo del navegador del usuario (`client-side`). La página no posee bases de datos SQL/NoSQL vulnerables, servidores intermedios, ni almacena logs de las consultas realizadas por los familiares.
2. **Mitigación de Información Maliciosa (Inyección/Sabotaje):** El sistema es de **Solo Lectura**. No existen formularios abiertos, botones de registro ni endpoints públicos donde usuarios externos puedan inyectar datos falsos o manipular las listas oficiales. 
3. **Control Centralizado de la Fuente:** El motor de búsqueda depende exclusivamente del archivo estático `pacientes.xlsx`. Solo el administrador del repositorio puede actualizar esta fuente binaria tras verificar los boletines oficiales emitidos por las direcciones de salud.
4. **Protección contra Extorsión:** El sistema indexa la información estrictamente necesaria para la localización de personas en contingencia (Nombres, Centros Asistenciales y Procedencia General), omitiendo números telefónicos privados de familiares o historiales clínicos críticos.

---

## ⚡ Características Técnicas

- **Procesamiento de Excel Nativo en Caliente:** Utiliza la librería **SheetJS** para decodificar directamente en la memoria del navegador el archivo maestro `pacientes.xlsx`, eliminando la necesidad de APIs o servicios backend de pago.
- **Búsqueda Indexada Instantánea:** Filtra por apellidos, nombres, números de cédula de identidad o sectores de procedencia a medida que el usuario escribe.
- **Filtro de Red Asistencial:** Clasificación dinámica automática basada en los centros médicos reportados en la pestaña consolidada de la fuente.

---

## 📂 Estructura del Repositorio

Para el correcto funcionamiento del software en entornos de producción (como **GitHub Pages**), el repositorio debe conservar la siguiente estructura en su rama principal (`main`):

```text
sismo-venezuela-2026/
├── index.html       # Aplicación y lógica del motor de búsqueda (interfaz de usuario)
└── pacientes.xlsx   # Libro consolidado oficial de Excel (origen de los datos)
