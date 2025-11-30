# Metodologia Integra Evolucionada v2.0 - Plantilla de Proyecto

Esta plantilla contiene todos los artefactos necesarios para implementar la **Metodologia Integra Evolucionada** en tus proyectos de desarrollo asistido por IA.

## Que es Integra Evolucionada

Integra Evolucionada es una metodologia de desarrollo colaborativo entre humanos y sistemas de IA, optimizada para proyectos que utilizan:
- Google Workspace (Docs, Sheets, Drive)
- Firebase (Firestore, Auth, Cloud Functions)
- Google Cloud Platform
- Herramientas externas (GitHub, Zapier, IONOS, etc.)

### Principios Fundamentales

1. **Flexibilidad Funcional**: Los roles de IA no son excluyentes; pueden apoyarse mutuamente.
2. **Principio del Canon y la Mosca**: Elegir la herramienta mas ligera que resuelva el problema eficientemente.
3. **Trazabilidad Total**: Cada cambio genera un registro en `Checkpoints/`.
4. **Codigo Auto-Documentado**: El codigo debe ser legible por si mismo; comentarios solo para decisiones no obvias.

## Roles de IA

### CODEX - Arquitecto de Soluciones e Implementador Principal
- Gestiona el proyecto y estructura SPECs.
- Valida entregables y genera PROYECTO.md.
- Implementa la mayoría de las tareas (código, docs, tests).
- Explica el porqué de cada decisión técnica.

### GEMINI CODE ASSIST - Revisor, Mentor y Segundo Implementador
- Propone optimizaciones y audita decisiones tecnicas.
- Verifica compatibilidad de dependencias y calidad del codigo.
- Aplica estrictamente las convenciones de `meta/SPEC-CODIGO.md`.
- Puede asumir tareas de CODEX (planificación e implementación) cuando se necesite una segunda opinión o se trabaje más pegado al ecosistema Google.

### FRANK - Director de Proyecto (humano)
- Supervisa, valida y aprueba entregables
- Su aprobacion convierte una tarea en estado `[X] Aprobado`
- No modifica estados en PROYECTO.md directamente

## 🆕 Novedades en v2.0

### Sistema de Gestión Avanzada
- **Estados Granulares**: 8 estados para tracking preciso ([ ] [~] [/] [V] [R] [✓] [X] + [!] [?])
- **Soft Gates**: 4 puertas de calidad obligatorias antes de completar tareas
- **Priorización Inteligente**: Metadatos, dependencias y fórmulas de priorización
- **Handoff entre Agentes**: Protocolo estructurado de comunicación

### Documentación Enriquecida
- **Checkpoints con Métricas**: Templates con decisiones técnicas y KPIs
- **ADR (Architecture Decision Records)**: Documentación de decisiones arquitectónicas
- **Versionado Semántico**: MAJOR.MINOR.PATCH formalizado

### Herramientas y Automatización
- **Dashboard Automático**: Script genera métricas visuales desde PROYECTO.md
- **Continue.dev Config**: Configuración lista para usar
- **Onboarding Guide**: Guía completa para nuevos agentes

## Como Usar Esta Plantilla

### 1. Copiar la Estructura

Copia todo el contenido de `metodologia-integra/` a la raiz de tu nuevo proyecto.

### 2. Adaptar Archivos de Plantilla

En la carpeta `templates/`:
- `PROYECTO.md.template` → Renombrar a `PROYECTO.md` y personalizar con tu backlog
- `.gitignore.template` → Renombrar a `.gitignore`
- `.env.example.template` → Renombrar a `.env.example` y agregar tus variables

### 3. Crear Estructura de Carpetas

```
tu-proyecto/
├── context/              # Contexto del proyecto
│   ├── 00_ARQUITECTURA_PROPUESTA.md
│   ├── dossier_tecnico.md
│   ├── SPEC-SEGURIDAD.md
│   ├── SPEC-TESTING.md
│   └── varios/
├── meta/                 # Metadatos y convenciones
│   ├── SPEC-CODIGO.md
│   ├── criterios_calidad.md
│   ├── plantilla_control.md
│   └── plantilla_SPEC.md
├── propuestas/          # Propuestas comerciales/tecnicas
├── Checkpoints/         # Historial de checkpoints
├── scripts/             # Scripts de automatizacion
├── api/                 # APIs y servicios
├── PROYECTO.md          # Archivo central de tareas
├── .gitignore
├── .env.example
└── arquitectura_distribuida_v_1.md
```

### 4. Configurar las IAs

#### Para ChatGPT (CODEX)
Carga el archivo `arquitectura_distribuida_v_1.md` como contexto inicial y proporciona:
```
Rol: CODEX (Arquitecto de Soluciones)
Objetivo: Gestionar el proyecto [NOMBRE] siguiendo Metodologia Integra Evolucionada
Contexto: [Breve descripcion del proyecto]
```

#### Para Gemini Code Assist (Revisor / Segundo Implementador)
Configúralo con acceso a:
- `meta/SPEC-CODIGO.md` (convenciones)
- `context/SPEC-SEGURIDAD.md`
- `context/SPEC-TESTING.md`

### 5. Iniciar el Workflow

1. **CODEX** crea el archivo `PROYECTO.md` con el backlog inicial
2. **CODEX** genera SPECs para las tareas complejas (usa `meta/plantilla_SPEC.md`)
3. **CODEX** ejecuta las tareas y actualiza estados en `PROYECTO.md`
4. **Gemini Code Assist** revisa código y, si hace falta, también puede implementar o ajustar código siguiendo los mismos SPECs
5. **FRANK** valida entregables y aprueba milestones

## Estructura de Archivos en Esta Plantilla

```
metodologia-integra/
├── README.md                           # Este archivo
├── arquitectura_distribuida_v_1.md    # Documento rector de la metodologia
├── meta/
│   ├── SPEC-CODIGO.md                 # Convenciones de codigo
│   ├── criterios_calidad.md           # Criterios de calidad
│   ├── plantilla_control.md           # Plantilla de checkpoints
│   └── plantilla_SPEC.md              # Plantilla de especificaciones
├── context/
│   ├── SPEC-SEGURIDAD.md              # Especificacion de seguridad
│   └── SPEC-TESTING.md                # Especificacion de testing
└── templates/
    ├── PROYECTO.md.template           # Plantilla de archivo central
    ├── .gitignore.template            # Plantilla de .gitignore
    └── .env.example.template          # Plantilla de variables de entorno
```

## Herramientas Recomendadas por Rol

- **CODEX**: ChatGPT / GitHub Copilot / otros LLMs
- **GEMINI CODE ASSIST**: Google Gemini Code Assist (revisión + implementación cuando se requiera)
- **Continue.dev**: Para contexto compartido entre agentes

### Editores y AI Coding Assistants
- **VS Code** con extension **Continue**
- **Cursor** (alternativa con IA integrada)
- **Gemini Code Assist** para Google Cloud Platform

### AI Chat Interfaces
- **ChatGPT** (rol CODEX/implementador principal)
- **Gemini Advanced / Gemini Code Assist** (revisor y posible segundo implementador)

### Control de Versiones
- **GitHub** (repositorios privados recomendados)
- **GitLab** (alternativa)

### Proyecto y Documentacion
- **Google Docs** para documentacion colaborativa
- **Google Sheets** para datos tabulares y seguimiento
- **Notion** (alternativa para documentacion)

## Flujo de Estados en PROYECTO.md

```
- [ ] Pendiente       # Tarea definida, no iniciada
- [/] En Progreso     # CODEX o GEMINI trabajando en la tarea
- [✓] Hecho           # Tarea completada y validada
- [X] Aprobado        # FRANK aprobo el entregable
```

## Buenas Practicas

### 1. Checkpoints Regulares
- Crea un checkpoint al final de cada sesion de trabajo
- Usa `meta/plantilla_control.md` como base
- Documenta decisiones tecnicas, riesgos y proximos pasos

### 2. SPECs Detallados
- Tareas complejas (>4h estimadas) requieren un SPEC
- Usa `meta/plantilla_SPEC.md`
- Incluye criterios de aceptacion medibles

### 3. Seguridad Desde el Inicio
- Nunca commitees archivos .env o .env.local
- Revisa `context/SPEC-SEGURIDAD.md` antes de deployment
- Ejecuta `pnpm audit` regularmente

### 4. Testing Continuo
- Sigue `context/SPEC-TESTING.md`
- Coverage minimo: 80% en logica de negocio
- Tests E2E para flujos criticos

### 5. Codigo Limpio
- Sigue `meta/SPEC-CODIGO.md` estrictamente
- Codigo auto-documentado > comentarios
- TypeScript con tipos explicitos en APIs publicas

## Soporte y Comunidad

Esta metodologia fue desarrollada por Frank Saavedra y el equipo de IAs: CODEX y Gemini Code Assist.

Para reportar problemas o contribuir mejoras:
1. Crea un issue en el repositorio de la plantilla
2. Propone cambios via Pull Request
3. Documenta casos de uso en `propuestas/`

## 📚 Documentación Completa

### Archivos Principales
- `arquitectura_distribuida_v_1.md` - Arquitectura completa del sistema
- `ONBOARDING.md` - Guía de inicio para nuevos agentes

### Gestión de Tareas
- `meta/sistema-estados.md` - Definición de 8 estados
- `meta/soft-gates.md` - 4 puertas de calidad
- `meta/sistema-priorizacion.md` - Priorización y metadatos
- `meta/sistema-handoff.md` - Protocolo de comunicación

### Calidad y Estándares
- `meta/SPEC-CODIGO.md` - Convenciones de código
- `meta/criterios_calidad.md` - Criterios de calidad
- `meta/plantilla_SPEC.md` - Template para SPECs
 - `context/SPEC-UX-UI.md` - Lineamientos para diseño UX/UI con herramientas externas (Stitch, Figma, etc.), siempre eligiendo la herramienta más adecuada según el contexto

### Documentación de Decisiones
- `context/decisions/README.md` - Sistema ADR
- `context/decisions/ADR-TEMPLATE.md` - Template ADR
- `context/decisions/ADR-001-ejemplo-uso-pnpm.md` - Ejemplo

### Checkpoints y Versionado
- `meta/plantilla-checkpoint-enriquecido.md` - Template de checkpoint
- `meta/versionado-semantico.md` - Reglas de versionado

### Automatización
- `scripts/generate-dashboard.js` - Generador de dashboard
- `templates/continuerc-template.json` - Config Continue.dev

## Changelog de la Metodologia

### v2.0 (2025-11-08)
- Sistema de gestión avanzada: 8 estados granulares, soft gates, priorización inteligente
- Protocolo de handoff estructurado entre agentes
- Checkpoints enriquecidos con métricas y decisiones técnicas
- Sistema ADR (Architecture Decision Records)
- Versionado semántico formalizado
- Dashboard automático de métricas
- Configuración Continue.dev lista para usar
- Guía completa de onboarding para nuevos agentes

### v1.2 (2025-11-08)
- Agregada seccion VII: Estándares de Codigo y Calidad
- Integracion de `meta/SPEC-CODIGO.md` como documento rector
- Actualizados artefactos obligatorios (SPECs de Seguridad, Testing, Codigo)
- GEMINI ahora aplica SPEC-CODIGO.md en cada revision

### v1.1 (original)
- Version inicial de Arquitectura Distribuida - Sistema Integra Evolucionada

---

**Version de la Plantilla:** 2.0  
**Fecha:** 2025-11-08  
**Autor:** Frank Saavedra (Director de Proyecto)  
**IAs Participantes:** CODEX y Gemini Code Assist
