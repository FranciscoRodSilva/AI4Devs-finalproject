> Detalla en esta sección los prompts principales utilizados durante la creación del proyecto, que justifiquen el uso de asistentes de código en todas las fases del ciclo de vida del desarrollo. Esperamos un máximo de 3 por sección, principalmente los de creación inicial o  los de corrección o adición de funcionalidades que consideres más relevantes.
Puedes añadir adicionalmente la conversación completa como link o archivo adjunto si así lo consideras


## Índice

1. [Descripción general del producto](#1-descripción-general-del-producto)
2. [Arquitectura del sistema](#2-arquitectura-del-sistema)
3. [Modelo de datos](#3-modelo-de-datos)
4. [Especificación de la API](#4-especificación-de-la-api)
5. [Historias de usuario](#5-historias-de-usuario)
6. [Tickets de trabajo](#6-tickets-de-trabajo)
7. [Pull requests](#7-pull-requests)

---

## 1. Descripción general del producto

**Prompt 1:** *(Gemini 3.1 Pro)*

```
Ayudame a generar las pregusntas correctas a un cliente para poder crear un sistema SaaS con el que pueda constriur desde 0 con Spec-Driven Development, debemos hacer las pregusntas a un cliente el cual tiene una constructora y no tiene un sistema para poder gestionarlo, como dato el cliente se mostro interesando en un sistema que le ofrecieron llamado "Diazar Business Intelligence" debemos poder ofreserle algo muy similar y tratar que con estas preguntas podamos lograr capturar todo lo que vaya a cubrir su necesidad.
```

*Este prompt generó el cuestionario (`Cuestionario_Requerimientos_SaaS_Construccion.docx`) que después se le envió realmente al cliente de la constructora. Sus respuestas son la fuente principal de todo el proyecto.*

**Prompt 1.1:** *(Gemini 3.1 Pro)*

```
Asume el rol de Product Owner experto en sistemas SaaS , queremos que se definan los objetivos y prioridades del proyecto así como las funciones prioritarias para el negocio, dicho esto necesito que revises a detalle el documento que se generó del cuestionario para la entrevista con dueño del negocio y me digas si es suficiente y cubre lo indispensable para iniciar el proyecto desde 0.
```

**Prompt 2:** *(Claude Code · Opus 5 · sesión "SaaS construcción: documentación técnica")*

```
@"D:\Documentos\Pako\Cuestionario_Requerimientos_SaaS_Construccion.docx"
Vamos a desarrollar un producto de software de inicio a fin, integrando IA en todas las fases: desde la idea y documentación, hasta el código, testing y despliegue. El objetivo es que apliques todo lo aprendido en el máster en un proyecto real y funcional.

Primero iremos por la Entrega 1 que es la Documentación técnica: Ficha del proyecto, descripción, arquitectura, modelo de datos, historias de usuario, tickets de trabajo.

El archivo principal de contexto es el cuestionario que se le hizo al cliente para ver sus necesidades que es Cuestionario_Requerimientos_SaaS_Construccion.docx

Qué incluye:

1.-Ficha del proyecto: nombre, descripción, URL del repo o ZIP (Lo que se genere del proyecto lo vamos a guardar en la siguiente ruta "D:\Documentos\LIDR\Proyecto Final" de manera local por el momento posteriormente una vez que se termine con todos los pasos aquí descritos y que todo este en orden se subirá a "https://github.com/FranciscoRodSilva/IA4Devs-Proyecto-Final.git" creando una rama llamada Entrega1)

2.-Descripción general del producto: objetivo, características, funcionalidades (Para esto te hare llegar unos archivos para que los analices muy bien y veas lo que se nos pide estos archivos los vas a encontrar en la siguiente dirección de la carpeta "D:\Documentos\LIDR\Proyecto Final\Doc de contexto")

3.-Arquitectura del sistema y modelo de datos (Una vez hecho el análisis del contexto del paso anterior hay que proponer cual es la mejor arquitectura para backend, frontend y base de datos que vayamos a usar en el proyecto, ten en cuenta que se tiene preferencia de usar React para el front y se quiere trabajar con python)

4.-Historias de usuario y tickets de trabajo (Una vez que tengamos completo el paso 2 basado en esto ayúdame a planificar entre 3 y 5 historias de usuario must-have (las imprescindibles) y 1-2 should-have las imprescindibles, también quiero que mee crees los tickets de trabajo realmente necesarios para iniciar el proyecto desde 0 para esto hay que apoyarse en la documentación cuando lleguemos a esta paso solicitame los archivos para que obtengas el contexto de como vamos a trabajar)

5.-Stack tecnológico elegido (En base a los pasos anteriores especialmente el 3 hay que proponer cual es la mejor Stack tecnológico que se puede utilizar para crear el proyecto)

Qué NO incluye todavía:
*Código. Esta entrega es 100% documentación.
*No propongas criterios de aceptación y que solo se acepte si cumple con los criterios descritos y que siempre sean los green no solo propangas el happy path se deben evaluar los errores.

Vamos a ir paso por paso cuando completes un paso dime revisamos los resultados y después te dire como y cuando pasar al siguiente paso.

Ten en cuenta que para el sistema queremos usar la metodología de SDD Spec-Driven Development.
```

*Primer prompt de la sesión de Claude Code. Fija el alcance completo de la Entrega 1 (los 5 pasos: ficha, descripción, arquitectura+modelo de datos, historias+tickets, stack) y la metodología SDD. De aquí salió el `README.md` con la ficha del proyecto.*

**Prompt 3:** *(Claude Code · Opus 5 · misma sesión)*

```
@"...Módulo 4\📄 La planificación cambia nuevos paradigmas 🔴.docx" @"...Módulo 4\📄 Anatomía de un backlog AI-ready 🔴.docx" @"...Módulo 4\📄 Estimación asistida por IA 🔴.docx" @"...Módulo 4\📄 PM tools + IA en 2026 🔴.docx" @"...Módulo 4\📄 Planificación ágil continua 🔴.docx" @"...Módulo 5\Documentación efectiva con IA.docx" @"...Módulo 5\📄 El déficit documental en la era IA 🔴.docx" @"...Módulo 5\📄 Arquitectura documentada ADRs + diagramas C4 con IA 🔴.docx" @"...Módulo 5\📄 Documentación de API y código 🔴.docx" @"...Módulo 5\📄 Testing de documentación en CI y docs para LLMs 🔴.docx"
continua con el paso 2, te voy a pasar archivos de contexto de como se va a manejar la documentacion y planificacion para que se tenga el contexto de como se quiere  trabajar en el sistema para tener todo preparado
```

*Arranca el Paso 2 aportando el material de los Módulos 4 y 5 del máster (planificación, backlog AI-ready, ADRs, C4). Generó `docs/01-descripcion-producto.md` (PRD), `docs/glosario.md` y `docs/convenciones.md`.*

---

## 2. Arquitectura del Sistema

### **2.1. Diagrama de arquitectura:**

**Prompt 1:** *(Claude Code · Opus 5 · sesión "SaaS construcción: documentación técnica")*

```
continua con el paso 3
```

*No fueron necesarios mas Prompt debido a que le habai especificado todo en los pasos anteriores*

*Confirmación breve tras cerrar el Paso 2. Dispara `docs/02-arquitectura.md` completo: drivers arquitectónicos, las tres vistas C4, contextos delimitados y los tres diagramas de secuencia de flujos clave.*

### **2.2. Descripción de componentes principales:**

**Prompt 1:** el mismo de 2.1 — *"continua con el paso 3"*, que define los 9 contextos delimitados, sus capas y sus dependencias.

**Prompt 2:** *(Claude Code · sesión "SaaS construcción: documentación técnica" · auditoría final)*

```
Revisa que todo este correcto y congruente en cuanto a lo que se refiere a la entrega que este todo completo y no contenga errores
```

*Auditoría de cierre de toda la Entrega 1. Sobre arquitectura, encontró y corrigió dos contradicciones reales: el flujo seguía describiendo el control presupuestal por partida (invalidado por `PA-01`, que lo movió a obra + tipo de partida) y sumaba la nómina al "consumido" por partida (invalidado por `PA-10`).*

### **2.3. Descripción de alto nivel del proyecto y estructura de ficheros**

*No hubo un prompt dedicado en exclusiva a la estructura de ficheros. La estructura del backend (`backend/cimenta/<modulo>/api · aplicacion · dominio · infraestructura`) se definió como parte del Paso 5 (stack tecnológico) — ver el Prompt 1 de la sección 2.4, que es el mismo que disparó esa parte del trabajo.*

### **2.4. Infraestructura y despliegue**

**Prompt 1:** *(Claude Code · sesión "SaaS construcción: documentación técnica")*

```
continua con el paso 5
```

*Arranca el Paso 5: stack tecnológico, `CLAUDE.md`, estructura de carpetas del backend y la sección de stack de `llms.txt`.*

**Prompt 2:** *(Claude Code · sesión "Revisión del stack tecnológico")*

```
Ahora vamos a revisar el stack tecnologico documentado para el proyecto es el mejor que se epuede usar ? tiene buena quimica trabajndo en conjunto y nos  aportara una aplicacion segura y robusta ?
```

*Arranca una sesión dedicada a auditar el stack ya elegido antes de dar la Entrega 1 por cerrada: compatibilidad entre piezas, seguridad y robustez.*

**Prompt 3:** *(Claude Code · sesión "CIMENTA Entrega 1 auditoría")*

```
No hay internet en la obra una vez qeu haya se deben actualizar los datos , actualiza ADR-011
```

*Introduce el requisito de captura sin conexión en obra. Generó `RNF-18`, el ADR-015 (captura diferida sin conexión) y la actualización del ADR-011.*

### **2.5. Seguridad**

**Prompt 1:** *(Claude Code · sesión "Revisión del stack tecnológico")*

```
aplica todo, empieza por la sección de seguridad
```

*Orden de aplicar las correcciones detectadas en la revisión de stack, empezando por seguridad. De aquí salió la sección de seguridad del PRD, el ADR de sesión con estado en servidor (ADR-014) y el endurecimiento de la autenticación (Argon2id, CSRF por doble envío).*

### **2.6. Tests**

*Esta entrega es 100% documentación: no hay tests de código todavía. Lo más cercano son los verificadores de documentación en CI (`tools/verificar_docs.py`, `tools/extraer_mermaid.py`), que nacieron del mismo prompt de auditoría citado en 2.2 (*"Revisa que todo este correcto y congruente..."*) al detectar que esas comprobaciones solo vivían en el scratchpad de la sesión y había que llevarlas al repositorio.*

---

### 3. Modelo de Datos

**Prompt 1:** *(Claude Code · sesión "SaaS construcción: documentación técnica")*

```
PA-01 es (b), PA-02 son dos cosas distintas, PA-03  se captura, PA-04 La nomina se hace corte los dias jueves se paga lo trabajado del dia viernes al jueves aun que se trabajen en obras distintas si se tiene que tner cuando y donde se trabajo el empleado, PA-05 es intencional porque no lo pueden acreditar y para ustedes es costo real esto puede pasar solo een algunas obras, PA-06 b, PA-07 se pone como parcialmente entregada y se reprograma el faltante hasta que la entreguen, PA-08 Es la c
```

*Respuestas del cliente a las 8 preguntas abiertas del PRD (`PA-01`…`PA-08`). Es el cambio de mayor impacto en el modelo de datos: introdujo la entidad `jornada`, dividió `explosion_partida` en `explosion_presupuesto`/`presupuesto_control`, movió el control presupuestal a nivel obra y elevó los invariantes de 14 a 18.*

**Prompt 2:** *(Claude Code · misma sesión)*

```
PA-10 si  y PA-11 basta por el momento
```

*Cierra las dos últimas preguntas abiertas del modelo (nómina sin repartir a partida; rendimiento observado por obra e insumo), dejando las 11 preguntas del PRD resueltas.*

**Prompt 3:** *(Claude Code · sesión "CIMENTA Entrega 1 auditoría")*

```
P1.a  ( A )
P1.b  ( B )              ← solo si P1.a = A
P1.c  ( A )                            ← confirmar con Dirección
P2    ( A )
P2.duda-cliente: conceptos no-M2 dentro de una partida → ( aceptable )
P5    ( C )
P6    ( B )
P6.política: subir un tope ya capturado → ( permitido con autorización )
P3    ( confirmo: personal)
P4    ( A )
```

*Segunda ronda de preguntas abiertas, ya en la auditoría de cierre. Estas decisiones (P1-P6) redefinieron la fórmula de `consumido`, el cálculo de avance físico, `m2_contrato` y la corrección de `presupuesto_control`, con impacto directo en tablas, invariantes y CTEs del modelo de datos.*

---

### 4. Especificación de la API

*En esta entrega (Entrega 1, 100% documentación, sin código ni despliegue) no se generó una especificación de API independiente — no hay OpenAPI/Swagger ni un documento de contrato de endpoints dedicado. Los contratos de API (incluido el contrato de error estructurado que usan todos los rechazos de reglas de negocio) se diseñaron como parte de `docs/02-arquitectura.md` §7.3, y el framework (FastAPI) quedó decidido en `docs/06-stack-tecnologico.md`. Cuando exista una entrega con código, esta sección se completará con los prompts que generen la especificación de la API en firme.*

---

### 5. Historias de Usuario

**Prompt 1:** *(Claude Code · sesión "SaaS construcción: documentación técnica")*

```
continua con el paso 4,  -Ejemplo de historias en gherkin:
Título de la Historia de Usuario: HDU-001 - Captura de personal

*Como* dueño *quiero* poder dar de alta, baja o realizar algún cambio en el personal que contrato *para* que pueda tener una base de datos de mi personal actualizada y fiable.

**Escenario 1: Apertura de formulario Empleados**
- **Dado que** el usuario quiere hacer alguna alta en el personal
- **Cuando** hace clic en el botón de +
- **Entonces** se abre la interfaz del formulario para llenar los datos del nuevo personal
- **Y** se posiciona el cursor sobre el primer campo a capturar.

**Escenario 2: Selección de puestos**
- **Dado que** el usuario quiere asignar un puesto
- **Cuando** hace click en el dropdown de puestos
- **Entonces** se abre el listado de los puestos activos previamente capturados en el formulario de puestos
- **Y** al seleccionar uno asignar al usuario.
y usa el contexto de los archivos para ver como crear los TKTs y lo demas
```

*Arranca el Paso 4, fijando el formato Gherkin en español (`HDU-XXX`, Dado que/Cuando/Entonces/Y) con un ejemplo real. Generó simultáneamente `docs/04-historias-usuario.md` y `docs/05-tickets-trabajo.md` (ver sección 6).*

**Prompt 2:** *(Claude Code · misma sesión)*

```
Antes de continuar con el paso 5 dale una revisada mas a fondo para las historias de usaurio que sean lo mas realistas y suficientes para cubrir necesidsades reales
```

*Pide una auditoría de suficiencia antes de cerrar. Encontró tres huecos de cadena (nada emitía la orden de compra, nada daba de alta personal, nada creaba obras/proveedores) y pasó de 7 a 9 historias (89 escenarios).*

**Prompt 3:** *(Claude Code · misma sesión)*

```
Revisaste si hay Historias Relacionadas y si las hay que realmente lo esten ?
```

*El borrador no tenía sección de historias relacionadas. Esta pregunta hizo construir 20 relaciones tipadas con evidencia, y detectó un riesgo real de doble conteo de mano de obra que derivó en la nueva regla `RN-22`.*

---

### 6. Tickets de Trabajo

**Prompt 1:** el mismo de la sección 5 — *"continua con el paso 4, [...] y usa el contexto de los archivos para ver como crear los TKTs y lo demas"*, que pide explícitamente generar los tickets junto con las historias. Disparó `docs/05-tickets-trabajo.md`.

**Prompt 2:** *(Claude Code · sesión "Revisión del stack tecnológico")*

```
confirma el RPO/RTO con Dirección General y asigna TKT-058 a un sprint
```

*Cierra un punto pendiente de planificación de sprints: fija el objetivo de recuperación ante desastres y ubica el ticket correspondiente en el sprint 7.*

**Prompt 3:** *(Claude Code · sesión "CIMENTA Entrega 1 auditoría")*

```
para sesion aparte pero dejalo documentado como pendiente
```

*Decide dejar fuera de esta sesión la descomposición de los tickets de captura sin conexión (surgida de `RNF-18`/ADR-015), pero exige documentarlo. Creó la sección "Pendiente de descomponer · captura sin conexión" en el backlog.*

---

### 7. Pull Requests

**Prompt 1:** *(Claude Code · sesión "Publicar en repositorio GitHub")*

```
Puedes publicar en GitHub en el Repositorio destino
```

*Primer prompt de la sesión de publicación. El asistente detecta que el repositorio destino es público y que `Doc de contexto/` contiene datos sensibles reales (nómina con nombres y salarios, presupuestos con precios unitarios de obra), y antes de hacer push resuelve cómo excluirla (`.gitignore`) sin perder la trazabilidad documental.*

**Prompt 2:** *(Claude Code · misma sesión)*

```
Crear PR y hacer Merge con produccion
```

*Con la rama `Entrega1` ya subida, pide crear el pull request hacia la rama por defecto (`Produccion`) y fusionarlo. Con este prompt se crea y se mergea el PR #1.*

