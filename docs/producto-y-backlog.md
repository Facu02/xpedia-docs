# XPedia — Definición de producto y backlog

> Documento vivo. Registra qué decidimos, por qué, qué existe hoy y qué falta.
> Última actualización: 2026-09-22

---

## 1. Qué es XPedia

Capacitación corporativa que se juega. La empresa sube su propia documentación (manuales, políticas, protocolos), un equipo de contenidos co-crea misiones con ayuda de IA, y los empleados las juegan en un entorno tipo RPG con progresión (XP, niveles, habilidades).

**La tesis central**: reemplazar el curso pasivo (video + multiple choice) por una simulación del trabajo real donde saber el procedimiento es lo que te hace bueno en el juego.

---

## 2. Objetivos

### Objetivo del proyecto académico
Probar que la gente vuelve a jugar **por gusto, no por obligación**, y que eso se traduce en una habilidad medible u observable.

### Objetivos de producto
- Reemplazar la capacitación pasiva por un ciclo de misiones con progresión medible.
- Que la IA genere contenido contextual a partir de la documentación real de cada empresa, en vez de cursos enlatados.
- Medir habilidades reales (comunicación, resolución, cumplimiento de protocolo) en vez de "completado / no completado".
- Darle al líder visibilidad accionable sin micro-gestión.

### Visión a largo plazo
Plataforma multi-empresa: L&D sube documentación → obtiene misiones generadas y revisadas → las despliega a su organización → recibe un dashboard accionable. Catálogo de mecánicas por tipo de habilidad.

---

## 3. No negociables

Estas reglas mandan por encima de cualquier decisión de diseño posterior.

1. **Cada decisión tiene reacción visible en el momento**, no solo al final. Sin esto es un formulario con skin.
2. **Toda mecánica simula un momento real del trabajo** — cero relleno genérico tipo "conectá los puntos para aprender empatía".
3. **Nada llega a un empleado real sin revisión humana.** La IA propone, una persona aprueba.
4. **El dato que le llega al admin sirve para actuar**, no es un "completó / no completó".
5. **El sistema reconoce contenido sensible y apaga la competencia automáticamente.** Nunca XP ni puntaje sobre temas como violencia de género, acoso o salud mental.

---

## 4. Decisiones tomadas

### 4.1 La IA vive en la autoría, no en el runtime ✅ DECIDIDO

La IA **no** corre en vivo mientras el empleado juega. Corre cuando el equipo de contenidos crea la misión: conversa con la IA, la IA propone el caso y el árbol de decisiones, un humano lo revisa y edita, y recién ahí queda "horneado" como contenido estático.

**Por qué**: más barato (sin costo por empleado por partida), más seguro (nada sin revisar llega a una persona real), más rápido (sin latencia en la partida), y sigue aprovechando la IA donde realmente acelera.

### 4.2 Pipeline de creación de contenido ✅ DECIDIDO

```
Documentación de la empresa
        ↓ (RAG)
Brief del caso (rol, habilidad, situación)
        ↓ (conversación con IA)
Borrador de misión generado
        ↓ (revisión y edición humana)
Misión publicada → la juegan los empleados
```

Estados de una misión: `Borrador` → `Generado por IA (sin revisar)` → `Editado` → `Publicado`.

### 4.3 Clasificación doble del contenido ✅ DECIDIDO

Al cargar un curso, se clasifica por **dos ejes independientes**:
- **Tipo** (qué mecánica le queda): interpersonal, procedimiento, verificación, operativo.
- **Sensibilidad** (si aplica el modo sensible).

La IA puede **sugerir** la sensibilidad como alerta, pero **nunca la decide sola** — la marca el funcional a mano.

### 4.4 Modo sensible ✅ DECIDIDO

No es un juego aparte, es un interruptor aplicable a cualquier mecánica:
- Sin timer, sin puntaje, sin competencia.
- Feedback de acompañamiento, no correcto/incorrecto.
- El jugador siempre es quien **responde** (compañero, líder, RRHH), nunca se simula a la víctima.
- Revisión obligatoria por alguien especializado (RRHH / legal / psicología), no un admin cualquiera.
- Incluye los canales reales de ayuda de la empresa.
- El empleado puede saltearlo sin que figure como "no completado" ante su manager.

### 4.5 Genericidad: motores + ficha de datos ✅ DECIDIDO

No se hace un juego por cliente. Se hacen **motores genéricos** (la mecánica) + una **ficha de datos abstracta** que la IA completa según la documentación de cada empresa. El mismo pipeline sirve para un reclamo de facturación y para un protocolo ISO.

### 4.6 Catálogo de mecánicas ✅ DECIDIDO (⚠️ en revisión, ver 4.7)

| Motor | Frase | Para qué contenido |
|---|---|---|
| **Diálogo con consecuencias** | "Lo que digas, importa" | Interpersonal: atención al cliente, ventas, liderazgo, conflictos |
| **Auditor** | "Encontrá lo que está mal" | ISO, seguridad, compliance, control de calidad |
| **Ronda** | "Recorré, y hacé lo que corresponde" | Apertura/cierre, bioseguridad, recepción de mercadería, checklists |
| **Crisis** | "Tenés 60 segundos" | Gestión de crisis, coordinación de equipos, operaciones |

### 4.7 🔄 GIRO IMPORTANTE: de 4 minijuegos a un turno de trabajo ⚠️ DECIDIDO, SIN CONSTRUIR

**El problema detectado**: los 4 motores, tal como estaban prototipados, son *multiple choice disfrazado*. El verbo del jugador siempre es "elegir la opción correcta de una lista finita". Eso no genera ganas de volver porque no hay nada que mejorar: o sabés la respuesta o no.

**Diagnóstico**: estábamos modelando *"¿qué harías vos?"* en vez de modelar **el trabajo en sí**.

**La nueva dirección**: el juego es **un turno de trabajo en tiempo real** (estilo Overcooked / Diner Dash aplicado al laburo). Los 4 motores dejan de ser juegos separados y pasan a ser **tipos de evento dentro del turno**:
- Llega un cliente difícil → diálogo, pero mientras los demás esperan.
- Ves algo fuera de norma al pasar → auditoría, pero decidiendo si parás o seguís.
- Hay que ejecutar un procedimiento → ronda, con cada paso ocupando segundos reales.
- Se cae el sistema → crisis.

**El mecanismo educativo clave**: saber el protocolo **te hace eficiente**, no "te da puntos". Los atajos se cobran sistémicamente más tarde:
- No verificaste identidad → a los 2 minutos vuelve rebotado y perdés 30 segundos con la cola llena.
- Apilaste cajas en la salida de emergencia → cuando hay que evacuar, tardás el triple.
- Abriste sin contar la caja → a las 3 de la tarde aparece un descuadre.

**Por qué esto sí da ganas de volver**: turnos cortos (2-3 min), eventos en orden aleatorio del mismo contenido, récord propio a superar, y sensación real de maestría.

### 4.8 Decisiones de UX ✅ DECIDIDO

- **Tonos claros**, nada de modo oscuro.
- **Sin mayúsculas persistentes** en la interfaz.
- Texto **alineado a izquierda** siguiendo el orden de lectura (títulos centrados sí).
- Stats como **pastillas estilo juego mobile** (ícono + número, sin etiquetas de texto): Lvl, XP %, casos resueltos, habilidad.
- **Poco texto**. Lo explicativo va detrás de un botón de ayuda, no en pantalla.
- Controles y ayuda **integrados al HUD**, no como chrome genérico de navegador.

### 4.9 Modelo de negocio (esbozo) 🟡 PARCIAL

- **Base**: los motores más genéricos (diálogo, medidor en vivo), que sirven a la mayoría de los rubros.
- **Extras pagos**: mecánicas más elaboradas o específicas de rubro, con estilo visual del cliente.
- Sin definir: si el pricing es por mecánica, por rubro, por cantidad de misiones o por usuario.

---

## 5. Estado actual — qué existe hoy

Todo lo construido son **prototipos jugables en HTML/Canvas** (single-file artifacts), no el stack productivo.

| Pieza | Estado | Qué hace |
|---|---|---|
| **Juego — Sucursal Telecom Sur** | ✅ Jugable | Mapa 2D pixel-art explorable, NPCs ambientales que entran y hacen fila, diálogo ramificado con un cliente, evaluación por rúbrica, XP/niveles/pastillas de stats, panel de ayuda |
| **Taller de Misiones** | ✅ Jugable | Carga de documentos (simulada), brief del caso, chat con IA que genera el árbol de diálogo, editor nodo por nodo, estados de publicación, vista previa |
| **Catálogo de motores** | ✅ Jugable | Los 4 motores en versión interactiva mínima, para comparar y validar mecánicas |

**Stack productivo definido pero no construido** (del README original): React + Phaser frontend, Java/Spring core, Python/FastAPI para IA, PostgreSQL + pgvector, Docker Compose.

---

## 6. Baches y preguntas abiertas

### 6.1 Baches de producto

| # | Bache | Impacto |
|---|---|---|
| B1 | **El giro al "turno" está decidido pero no construido.** Todo lo jugable hoy sigue siendo la versión multiple-choice | 🔴 Alto — es el corazón de la tesis |
| B2 | **Nunca lo probó un usuario real.** Todas las conclusiones de "esto engancha / no engancha" son intuición nuestra | 🔴 Alto |
| B3 | **No hay forma de medir aprendizaje**, solo proxies de enganche (XP, casos resueltos) | 🔴 Alto — el objetivo declarado es habilidad medible |
| B4 | **Modo sensible definido, no implementado** en ninguna pieza | 🟡 Medio |
| B5 | **Clasificación automática de contenido** (qué motor le queda a un documento) no existe en el Taller | 🟡 Medio |
| B6 | **Vista de admin / progreso** no existe ni como mockup | 🟡 Medio |
| B7 | **Árbol de habilidades** no existe. Sin definir si es cosmético o desbloquea contenido real | 🟡 Medio |
| B8 | **Mundo con varias misiones** — hoy hay una sola misión y un solo mapa | 🟢 Bajo por ahora |

### 6.2 Baches técnicos

| # | Bache | Impacto |
|---|---|---|
| T1 | **No hay backend.** Todo es frontend con datos mockeados | 🔴 Alto |
| T2 | **El RAG no existe** — la carga de documentos del Taller es simulada | 🔴 Alto |
| T3 | **No hay persistencia real** — el progreso vive en memoria de sesión | 🔴 Alto |
| T4 | **No hay multi-tenant ni autenticación** | 🟡 Medio |
| T5 | **No hay modelo de datos SQL detallado** (tipos, FKs, índices) | 🟡 Medio |
| T6 | **No hay contrato de API** entre servicio core y servicio IA | 🟡 Medio |
| T7 | **No existe el repo con docker-compose** funcional | 🟡 Medio |

### 6.3 Preguntas abiertas para debatir

1. **¿Hasta dónde llevamos el tiempo real en el turno?** Riesgo: si se vuelve muy frenético deja de parecer herramienta corporativa y RRHH no lo compra. Instinto actual: exigente pero no arcade — presión por acumulación, no por reflejos.
2. **¿El árbol de habilidades es cosmético o desbloquea contenido?** Lo segundo es más interesante pero implica diseñar contenido por rama.
3. **¿El admin ve el detalle de cada simulación individual o solo agregados?** Si el empleado siente vigilancia conversación por conversación, se rompe la gamificación.
4. **¿Quién define qué motor usa cada curso** — la IA sola, el funcional a mano, o la IA sugiere y el humano confirma?
5. **Pricing de los extras**: ¿por mecánica, por rubro, por volumen?

---

## 7. Backlog

Ordenado por lo que más reduce incertidumbre primero.

### Épica A — Validar que el turno es divertido 🔴 Prioridad máxima

| ID | Item | Notas |
|---|---|---|
| A1 | Prototipo del turno en tiempo real sobre la sucursal existente | Reusa mapa, movimiento y NPCs ya construidos |
| A2 | Sistema de eventos que llegan solos (clientes, teléfono, papeleo) | Con frecuencia configurable |
| A3 | Acciones con duración real (caminar tarda, procedimientos ocupan segundos) | El corazón de la escasez |
| A4 | Medidores que decaen (paciencia por cliente, estrés propio) | |
| A5 | Consecuencias sistémicas diferidas (el atajo se cobra después, no al instante) | Lo que diferencia esto de un quiz |
| A6 | Score final del turno + récord personal | Motor de rejugabilidad |
| A7 | **Testear con 5-10 personas reales** y medir si vuelven a jugar sin que se lo pidan | Cierra B2 |

### Épica B — Medir aprendizaje de verdad

| ID | Item |
|---|---|
| B1 | Definir qué métrica representa "aprendió" (¿eficiencia del turno subiendo con las repeticiones?) |
| B2 | Registrar por partida: atajos tomados, protocolos cumplidos, tiempo por tarea |
| B3 | Comparativa primera partida vs. quinta partida del mismo empleado |

### Épica C — Taller de misiones productivo

| ID | Item |
|---|---|
| C1 | Carga real de documentos + ingesta a RAG (pgvector) |
| C2 | Clasificador de tipo de contenido (qué motor le corresponde) |
| C3 | Clasificador/alerta de sensibilidad + marcado manual del funcional |
| C4 | Generación del contenido del turno (estaciones, tareas, duraciones, eventos) — no solo árboles de diálogo |
| C5 | Flujo de aprobación con rol de revisor especializado para contenido sensible |

### Épica D — Vista de admin

| ID | Item |
|---|---|
| D1 | Definir qué ve el admin (agregados vs. individual) — resolver pregunta abierta #3 |
| D2 | Mockup de la vista priorizada por "necesita atención", no tabla plana |
| D3 | Respetar el opt-out de modo sensible (no figurar como incompleto) |

### Épica E — Progresión y mundo

| ID | Item |
|---|---|
| E1 | Definir si el árbol de habilidades desbloquea contenido — resolver pregunta abierta #2 |
| E2 | Árbol de habilidades visual, alimentado por los puntos de rúbrica que ya calculamos |
| E3 | Mundo con múltiples escenarios/misiones navegables |

### Épica F — Infraestructura

| ID | Item |
|---|---|
| F1 | Esqueleto de repo + docker-compose funcional |
| F2 | Modelo de datos SQL detallado |
| F3 | Contrato de API entre core (Java) y servicio IA (Python) |
| F4 | Autenticación y multi-tenant |
| F5 | Persistencia real del progreso |

---

## 8. Roadmap de entregas

| Entrega | Contenido | Estado |
|---|---|---|
| **E0** | Prototipo jugable del diálogo + mapa. Valida la idea base | ✅ Hecho |
| **E1** | Taller de misiones (autoría asistida por IA + human-in-the-loop) | ✅ Hecho |
| **E2** | Catálogo de mecánicas jugables | ✅ Hecho |
| **E3** | **Prototipo del turno + test con usuarios reales** | ⬅️ Siguiente |
| **E4** | Taller generando contenido de turno + RAG real | Pendiente |
| **E5** | Vista de admin con foco en mejora | Pendiente |
| **E6** | Árbol de habilidades + mundo con varias misiones | Pendiente |
| **E7** | Piloto real con datos de enganche para la tesis | Pendiente |

---

## 9. Bitácora de cambios de rumbo

Vale la pena registrar los giros, porque son lo más valioso para defender el proyecto.

| Fecha | Cambio | Motivo |
|---|---|---|
| 2026-09 | IA sale del runtime, pasa a la autoría | Costo, seguridad, latencia; y "la IA es la herramienta, no el foco" |
| 2026-09 | Una mecánica única → catálogo de 4 motores | Un protocolo ISO no es una conversación; forzarlo a diálogo se siente impostado |
| 2026-09 | Ordenar tarjetas → recorrer estaciones (Ronda) | El puzzle de ordenar se sentía de escritorio, no de estar parado en el protocolo |
| 2026-09 | **4 minijuegos → un turno de trabajo** | Todos los motores eran multiple choice disfrazado; no había nada que mejorar con la práctica |
