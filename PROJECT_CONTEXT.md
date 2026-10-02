# XQSME — Project Context & Analysis

> Este archivo sirve como memoria del proyecto. Se actualiza a medida que avanza el análisis, el equipo y el desarrollo.

---

## ¿Qué es XQSME?

XQSME es una plataforma de **Hardware + SaaS** para restaurantes. La idea central es reducir el costo de atender una mesa mientras aumenta el revenue generado por esa mesa.

El producto combina:
- Un **dispositivo físico** en cada mesa (micrófono array + parlante + Raspberry Pi + Wi-Fi)
- Una **plataforma cloud** que procesa la voz, conversa con el cliente y estructura el pedido
- Un **sistema operativo para restaurantes** (menú, mesas, cocina, usuarios, dispositivos)
- Un **motor de revenue** con upselling por IA, métricas y atribución de conversiones

**Tagline interno:** *"Hardware is the interface. ROI data is the product. The software and dataset are the asset."*

---

## Estado actual del proyecto

- Etapa: **concepto / pre-MVP**
- Tienen: deck de negocio bien armado, arquitectura técnica definida en papel, MVP visual de la página (básico)
- No tienen: producto funcionando, código productivo, equipo completo

---

## Arquitectura técnica definida (en papel)

```
Cliente habla
     ↓
Hardware XQSME (Raspberry Pi + matriz 4 micrófonos + altavoz)
     ↓
GPT-Live (voz en tiempo real, entiende y estructura el pedido)
     ↓
Backend XQSME Cloud (API segura, base de datos, lógica de negocio, gestión de pedidos)
     ↓
KDS - Kitchen Display System (pantalla de cocina en tiempo real)
     ↓
Dashboard restaurante (seguimiento, historial, métricas)
```

### Componentes del dispositivo
- Matriz de 4 micrófonos
- Altavoz integrado
- Raspberry Pi + módulos de audio
- Conexión HTTPS/TLS
- LED + botón de ayuda física

### Componentes del sistema cloud
- API segura
- Base de datos
- Gestión de pedidos
- Lógica de negocio
- Integraciones (POS, pagos)

---

## Los tres productos

| Producto | Descripción |
|---|---|
| **XQSME Device** | Interfaz de voz en la mesa. Mic array, speaker, LED, botón, Wi-Fi, device ID. |
| **XQSME OS** | Capa operativa del restaurante. Menú, mesas, KDS, estados, usuarios, dispositivos. |
| **Revenue Engine** | Inteligencia comercial. Reglas de upsell, datos de conversión, atribución de revenue. |

---

## Propuesta de valor (ROI para el restaurante)

- Reducción de staff de atención: ejemplo de 18 → 8 personas
- Ahorro mensual ejemplo: US$7,500 (10 personas × US$750/mes)
- Costo SaaS plan Growth: US$1,799/mes
- **Beneficio neto ilustrativo: US$5,701/mes** antes de considerar uplift de revenue

### Dashboard del dueño incluye:
- Estado en vivo de las mesas
- Revenue por mesa y ticket promedio
- Revenue atribuido a IA
- Tasa de conversión de upsell
- Tasa de intervención humana
- Uptime del dispositivo y costo de IA por pedido

---

## Piloto diseñado

- 10 restaurantes (segmento premium y mid-high)
- 100 dispositivos (~10 mesas por restaurante)
- Baseline de 30-60 días antes de instalación
- Métricas: payroll, revenue, ticket promedio, errores de pedido, intervención humana, revenue de upsell, satisfacción del cliente

---

## Riesgos identificados

| Riesgo | Mitigación definida |
|---|---|
| Alérgenos | Solo datos verificados por el restaurante; escalar a humano si hay incertidumbre |
| Privacidad | Botón mute físico, sesiones cortas, retención limitada |
| Fallback | Botón de ayuda física + alerta en dashboard |
| Competencia | POS incumbentes, copias low-cost, agentes de voz de big tech |
| Adopción | Riesgo latente, no resuelto aún |

---

## Equipo (en formación)

| Rol | Persona | Notas |
|---|---|---|
| Tech Lead + Fullstack Dev + UX/UI | Julian (yo) | Full time. Lidera producto y arquitectura. Cubre Fases 1, 2 y 3. |
| Backend / DevOps / Integraciones | Amigo dev | Medio tiempo. Perfil backend, infra cloud, integraciones POS y seguridad. |
| Project Manager | Amigo PM | Coordinación, cliente, prioridades. Número a definir por separado. |
| Ingeniero Embebido / IoT | Por contratar / tercerizar | Requerido para Fase 4 (firmware ESP32-S3, DSP, audio, OTA). Perfil muy específico. |

---

## Análisis del scope técnico

### Lo que cubre Julian (Tech Lead + Fullstack + UX/UI) — Fases 1, 2 y 3
- Todo el frontend y UX/UI
- APIs y lógica de negocio del backend web
- Base de datos y modelos de datos (PostgreSQL)
- Dashboard y KDS en tiempo real (WebSockets)
- Panel de administración del menú y catálogo
- Sistema de upselling con reglas configurables
- Arquitectura del sistema completo
- Coordinación técnica con proveedor de firmware (Fase 4)
- QA e integración final backend↔dispositivo

### Lo que cubre el amigo dev (Backend / Infra) — Fases 1 y 3 principalmente
- Pipeline de voz en tiempo real (latencia, WebSockets bidireccional)
- Integración con APIs de voz (OpenAI Realtime, Whisper)
- Infraestructura cloud y DevOps
- Integraciones con POS (Toast, Square, etc.)
- Seguridad de pagos
- Colas de eventos e idempotencia

### Lo que requiere proveedor tercerizado (Fase 4)
- Firmware sobre ESP32-S3 (o equivalente)
- DSP: cancelación de eco (AEC), beamforming, DoA, supresión de ruido
- Transmisión segura de audio (I2S → WebSockets/TLS)
- Control de LEDs, botones físicos, altavoz
- Aprovisionamiento Wi-Fi y gestión de flota (OTA)

---

## Roadmap oficial del proyecto

El cliente entregó un documento de especificación técnica con **34 semanas** como marco de tiempo total. El proyecto está dividido en 4 fases secuenciales:

| Fase | Descripción | Responsable |
|---|---|---|
| **Fase 1** | Motor conversacional core + backend transaccional (WebSockets, PostgreSQL, function calling) | Equipo interno |
| **Fase 2** | Plataforma operativa + dashboards (KDS táctil, consola de admin, reportes, roles) | Equipo interno |
| **Fase 3** | Conectores POS + impresión térmica ESC/POS + pasarela de pagos | Equipo interno |
| **Fase 4** | Firmware embebido (ESP32-S3, DSP, beamforming, AEC, OTA) + hardware físico del dispositivo | **Tercerizado** — requiere ingeniero embebido/IoT especializado |

### Estructura de dos tracks
- **Track Software (Fases 1–3):** Equipo interno. ~24–26 semanas (~6 meses).
- **Track Hardware/Firmware (Fase 4):** Proveedor externo especializado. Idealmente arranca en paralelo desde la Fase 2. ~10–12 semanas.
- **Integración final + QA:** ~4 semanas (semanas 31–34). Julian participa en criterios de aceptación y testing de integración backend↔dispositivo.

---

## Estimación de desarrollo

**~6 meses** para el Track Software (Fases 1–3 + integración). Marco total del proyecto: **34 semanas** incluyendo hardware.

---

## Presupuesto — Equipo Dev Interno (acordado)

### Sueldos mensuales confirmados

| Persona | Rol | Dedicación | Sueldo mensual |
|---|---|---|---|
| **Julian** | Tech Lead + Fullstack + UX/UI | Full time | **$2,350 / mes** |
| **Amigo dev** | Backend + Infraestructura + Integraciones | Medio tiempo | **$1,450 / mes** |
| PM | Project Manager | — | A definir por separado (fuera del scope dev) |

**Total equipo dev / mes: $3,800**

### Costo equipo dev a 6 meses

| Persona | × 6 meses | Total |
|---|---|---|
| Julian | $2,350 × 6 | $14,100 |
| Amigo dev | $1,450 × 6 | $8,700 |
| **Subtotal equipo** | | **$22,800** |

---

## Costos operativos estimados (supuestos)

### APIs de IA / Voz (etapa desarrollo)
| Servicio | Estimado / mes |
|---|---|
| OpenAI GPT-4o / Realtime API | $150 – $400 |
| Whisper API (fallback/pruebas) | $50 – $100 |
| **Total APIs IA** | **~$200 – $500 / mes** |

> En producción (piloto 10 restaurantes) puede subir a $800–$2,000/mes. Va en el modelo de pricing al cliente.

### Infraestructura cloud
| Etapa | Costo estimado / mes |
|---|---|
| Fases 1–2 (desarrollo/testing) | $40 – $80 |
| Fase 3 + staging | $120 – $250 |
| Piloto producción (10 restaurantes) | $300 – $600 |

### Herramientas y licencias
| Concepto | Estimado / mes |
|---|---|
| GitHub, Figma, herramientas IA, misc | $65 – $125 |

---

## Presupuesto global del proyecto

| Concepto | Estimado total |
|---|---|
| Equipo dev interno (6 meses) | $22,800 |
| APIs de IA (desarrollo, 6 meses) | $1,200 – $3,000 |
| Infraestructura cloud (6 meses) | $700 – $1,500 |
| Herramientas y licencias (6 meses) | $400 – $750 |
| **Track Software total** | **~$25,100 – $28,050** |
| Track Hardware/Firmware (tercerizado) | $10,000 – $20,000 |
| Contingencia (~10%) | $3,500 – $4,800 |
| **Total estimado del proyecto** | **~$38,600 – $52,850** |

> Budget cliente estimado: ~$100,000 USD. Queda margen para hardware del piloto (100 dispositivos), PM, operación post-lanzamiento y contingencias.

### Táctica de negociación (referencia)
- Julian llegó con número propio: **$2,500/mes** — acordado en **$2,350/mes**
- Amigo dev: acordado en **$1,450/mes** (medio tiempo)

---

## Notas y decisiones pendientes

- [ ] Definir stack tecnológico concreto (Next.js? Node/TypeScript? PostgreSQL? Railway/DO?)
- [ ] Revisar el demo/código del MVP actual que enviará el cliente
- [ ] Definir modelo de contratación formal (mensual fijo por ahora, posible por hitos)
- [ ] Revisar el MVP visual actual y definir qué se rescata
- [ ] Buscar/cotizar proveedor especializado en firmware/IoT para Fase 4
- [ ] Validar estimación de costos de infra y APIs con amigo dev (especialmente Fase 3 — integraciones POS)
- [ ] Presentar propuesta al cliente con desglose de dos tracks
- [ ] Definir número del PM (fuera del scope dev, lo maneja él)

---

*Última actualización: roadmap 34 semanas recibido, presupuesto acordado (Julian $2,350 + amigo dev $1,450), estructura de dos tracks definida — sesión con Kiro AI*
