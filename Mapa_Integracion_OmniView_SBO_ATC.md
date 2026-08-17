# Mapa de integración hacia SBO

La experiencia entregada es una simulación de interfaz. Para convertirla en un piloto funcional deben reemplazarse los datos locales por adaptadores a los servicios productivos de SBO y del ecosistema técnico de ATC.

## Arquitectura propuesta

```text
Cámaras / sensores / analítica de ATC
                  │
                  ▼
       Adaptador de ingreso de eventos
                  │
                  ▼
     Motor de alarmas y reglas de SBO
          │        │        │
          │        │        └── Contactos y escalamiento
          │        └─────────── Planes de acción
          └──────────────────── VMS / video / evidencia
                  │
                  ▼
   Espacio operativo + historial + métricas
```

## Adaptadores requeridos

| Componente | La demo simula | Para el piloto se debe validar |
|---|---|---|
| Ingreso de alarmas | Evento de cruce de línea | Protocolo/API disponible, esquema, deduplicación y prioridades |
| Video | Archivo MP4 local | VMS, autenticación, streams, playback y retención |
| Analítica | Persona/zona/confianza | Proveedor, tipos de evento, zonas y umbrales reales |
| Plan de acción | Flujo perimetral de 5 pasos | SOP de ATC, permisos por rol y excepciones |
| Disuasión | Botones de voz y sirena | Dispositivos, comandos, confirmación de ejecución y fallas |
| Escalamiento | Alpha III + contacto del sitio | Canales autorizados, directorio, horarios y acuses |
| Evidencia | JSON descargable | API, almacenamiento, hashes, retención y permisos |
| Métricas | Tiempos ilustrativos | SLA, taxonomía, tableros y campos auditables |

## Supuestos que la visita debe validar

- El alcance perimetral representa aproximadamente el 95 % de los casos objetivo comentados por el prospecto.
- La central puede recibir o exponer eventos con suficiente contexto para correlacionarlos con video y ubicación.
- Los protocolos de disuasión y escalamiento varían por sitio, horario y cliente.
- La coordinación con Alpha III/Carabineros debe representarse como un flujo autorizado, no como una integración asumida.
- Los nombres, números, ubicaciones y tiempos mostrados en la demo son ilustrativos.

## Criterios para un piloto medible

- Tiempo desde evento hasta toma de atención.
- Tiempo de verificación y porcentaje de falsas alarmas.
- Cumplimiento del plan de acción.
- Confirmación de acciones remotas.
- Tiempo y éxito del escalamiento.
- Integridad del expediente por incidente.

## Seguridad y operación

- Mantener secretos y endpoints fuera del repositorio; usar variables de entorno.
- Separar ambientes demo, staging y producción.
- Aplicar control de acceso por rol y trazabilidad de operador.
- Registrar fallas de cámara, stream, acción y comunicación como estados explícitos.
- Definir retención, privacidad y acceso a imágenes de acuerdo con la operación de ATC y la normativa aplicable.
