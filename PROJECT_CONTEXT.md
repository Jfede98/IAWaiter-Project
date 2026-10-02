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
| Fullstack Dev + UX/UI Lead | Julian (yo) | Fuerte en frontend, diseño y UX. Cubre backend web con apoyo de IA. |
| Project Manager | Amigo PM | Coordinación, cliente, prioridades. |
| Backend / DevOps / Seguridad | Por confirmar | Perfil necesario para voz en tiempo real, infra cloud, integraciones POS y seguridad. |

---

## Análisis del scope técnico

### Lo que cubre Julian (Fullstack + UX Lead)
- Todo el frontend y UX/UI
- APIs y lógica de negocio del backend web
- Base de datos y modelos de datos
- Dashboard y KDS en tiempo real (WebSockets)
- Panel de administración del menú
- Sistema de upselling con reglas configurables

### Lo que requiere el perfil adicional (Backend/DevOps)
- Firmware / app del dispositivo (Raspberry Pi, audio)
- Integración de voz en tiempo real (latencia, Whisper, GPT-Live)
- Seguridad de pagos
- Integraciones con POS (Toast, Square, etc.)
- Infraestructura cloud y DevOps

---

## Estimación de desarrollo

Con equipo pequeño (2-3 devs): **4 a 6 meses** para un MVP funcional piloteable.

---

## Presupuesto estimado del equipo

### Contexto
- Inversión del cliente (extraoficial): ~$100,000 USD
- Cliente vive en el exterior, paga en USD
- Equipo basado en Ecuador
- Duración estimada del proyecto: 4-6 meses
- El equipo usará herramientas de IA para trabajar de forma eficiente

### Rangos de mercado — Dev mid en Ecuador pagado en USD
Un dev mid con 3-4 años de experiencia trabajando para cliente extranjero en USD: **$1,500 - $3,000/mes**

### Propuesta de sueldos mensuales

| Persona | Rol | Sueldo sugerido | Justificación |
|---|---|---|---|
| **Julian** | Fullstack + UX/UI Lead | **$2,200 - $2,500** | Más horas disponibles, doble perfil (dev + UX), lidera el producto |
| Amigo dev | Backend / Conexiones | $1,800 - $2,000 | Menos horas disponibles, perfil más específico |
| Amigo PM | Project Manager | $1,500 - $1,800 | Coordinación, manejo del cliente |

### Totales estimados
- **Por mes (equipo completo):** ~$5,500 - $6,300
- **A 5 meses:** ~$27,500 - $31,500
- Deja margen dentro de los $100k para hardware del piloto, infraestructura cloud, herramientas y contingencias

### Táctica de negociación
- No llegar preguntando cuánto pagan — llegar con número propio primero
- Número de apertura para Julian: **$2,500/mes**
- Si hay presión hacia abajo, el piso es $2,000
- El argumento es: doble perfil (fullstack + UX), mayor dedicación horaria, y uso de IA como multiplicador de productividad

---

## Notas y decisiones pendientes

- [ ] Definir stack tecnológico concreto (Next.js? Node? Python backend? AWS/GCP?)
- [ ] Confirmar incorporación del amigo dev (backend/conexiones) al equipo
- [ ] Revisar el demo/código del MVP actual que enviará el cliente
- [ ] Definir modelo de contratación formal (mensual fijo por ahora)
- [ ] Hablar con el PM (amigo) para alinear números antes de ir al cliente
- [ ] Revisar el MVP visual actual y definir qué se rescata

---

*Última actualización: análisis de presupuesto y equipo — sesión con Kiro AI*
