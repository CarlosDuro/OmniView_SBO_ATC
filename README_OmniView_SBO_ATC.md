# OmniView SBO · Demo para Alguien te Cuida

Experiencia operativa interactiva que muestra cómo OmniView/OmniCloud puede complementar la central de monitoreo de **Alguien te Cuida (ATC)** en escenarios de seguridad perimetral.

La interfaz toma como referencia el lenguaje visual y el patrón de trabajo de SBO: alerta emergente, cola operativa, video contextual, plan de acción, escalamiento y expediente del incidente. El objetivo es demostrar valor antes de la visita técnica y abrir una conversación informada sobre la operación real.

> Esta es una simulación comercial de front-end. No se conecta a cámaras, VMS, Carabineros, Alpha III, telefonía ni servicios productivos de SBO.

## Qué se puede demostrar

- Recepción de una alerta perimetral priorizada.
- Verificación con video, analítica, ubicación y contexto en un solo espacio.
- Decisión del operador: confirmar intrusión o cerrar como falsa alarma.
- Disuasión simulada mediante advertencia por voz y sirena.
- Escalamiento coordinado a Alpha III/Carabineros y al contacto del sitio.
- Cierre con métricas, línea de tiempo y expediente descargable en JSON.
- Historial de alarmas con detalle y trazabilidad.
- Historial de eventos analíticos con o sin alarma.
- Conversión de un evento analítico en una nueva alarma.
- Reinicio inmediato para repetir la demostración.

## Ejecutar localmente

La entrega ya está compilada y no requiere instalar dependencias. Como usa módulos del navegador, debe abrirse desde un servidor web estático, no mediante doble clic sobre `index.html`.

Con Python instalado, abre una terminal dentro de la carpeta y ejecuta:

```bash
python -m http.server 8080
```

Después visita `http://localhost:8080`. Para una grabación limpia se recomienda una ventana de **1600 × 900** o **1920 × 1080**, con zoom del navegador entre 90 % y 100 %.

## Contenido de la entrega

Todos los archivos están en la raíz; el paquete no contiene subcarpetas:

- `index.html`: punto de entrada.
- `app.js`: experiencia y lógica de la simulación.
- `styles.css`: sistema visual SBO/ATC.
- `atc-perimeter-demo.mp4`: video proporcionado por ATC.
- `frame-*.jpg`: fotogramas para evidencias e historiales.
- `Guion_Grabacion_OmniView_SBO_ATC.md`: recorrido sugerido para el video comercial.
- `Mapa_Integracion_OmniView_SBO_ATC.md`: mapa hacia un piloto real.

## Subir a GitHub

1. Crea un repositorio vacío.
2. Copia todos los archivos de esta entrega directamente en la raíz del repositorio.
3. Publica la raíz como sitio estático en GitHub Pages o en el mecanismo de carga de SBO.

No se requiere un proceso de compilación adicional.

## Preparación para SBO

La demo está separada de cualquier backend para que pueda presentarse sin riesgo. Para convertirla en piloto se deben mapear los adaptadores descritos en `Mapa_Integracion_OmniView_SBO_ATC.md`: ingreso de alarmas, streams del VMS, acciones remotas, contactos y persistencia de evidencias.

## Uso comercial

El relato recomendado no es “reemplazar la operación actual”, sino **orquestar y documentar la respuesta** sobre la infraestructura que ATC ya utiliza. La demostración se concentra en el 95 % de escenarios perimetrales mencionado por el prospecto y deja explícitos los supuestos que deberán validarse durante la visita a Chile.
