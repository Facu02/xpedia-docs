# XPedia — Plan de sprints y capacidad

> Acompaña a `XPedia-Capacidad-Backlog-Sprints.xlsx`.
> Acá va el *por qué* de los números; el Excel es el artefacto de la entrega.
> Última actualización: 2026-09-22

---

## 1. Parámetros de planificación

| Variable | Valor | De dónde sale |
|---|---|---|
| Integrantes | 7 | Equipo actual |
| Dedicación declarada | 14 hs/semana por persona | Valor ideal del equipo, se reajusta con el velocity real |
| Sprints | 4 (1 MVP por sprint) | Un MVP por entrega |
| Duración de sprint | 18 días | Los 72 días entre el 24/09 y el 04/12 divididos en 4 partes iguales |
| Factor de no planificados | 0,15 | Default del template de la cátedra |
| **Capacidad ideal por sprint** | **252 hs** | 7 × 14 × 18/7 |
| **Capacidad neta por sprint** | **214 hs** | 252 × 0,85 |
| **Capacidad neta del proyecto** | **856 hs** | 214 × 4 |

El patrón diario por persona es 1-1-1-2-2-4-3 (lunes a domingo) = 14 hs. Poco entre
semana, fuerte el fin de semana. Es lo que se sostiene con gente que cursa y trabaja, y
es lo que alimenta el burndown planificado del Sprint 1.

## 2. Calendario

| Sprint | MVP | Inicio | Fin |
|---|---|---|---|
| Sprint-Nro1 | MVP 1 | jue 24/09/2026 | dom 11/10/2026 |
| Sprint-Nro2 | MVP 2 | lun 12/10/2026 | jue 29/10/2026 |
| Sprint-Nro3 | MVP 3 | vie 30/10/2026 | lun 16/11/2026 |
| Sprint-Nro4 | MVP 4 | mar 17/11/2026 | **vie 04/12/2026** |

El Sprint 4 cierra exactamente en la fecha de la última entrega.

## 3. Qué es cada MVP

El criterio de orden es el mismo del backlog original: **primero lo que más reduce
incertidumbre**. Por eso el turno jugable (el giro de la sección 4.7) entra en el
Sprint 2 y no más tarde: es el corazón de la tesis y el bache B1.

### MVP 1 — Idea cerrada y todo mockeado (Sprint 1, 214 hs, 15 PBIs)

Cero backend. Todas las pantallas del producto existen y se pueden recorrer, pero están
hardcodeadas. Es un **walking skeleton visual**: se ve el producto completo de punta a
punta antes de construir nada.

Incluye: definición de producto cerrada (las 5 preguntas abiertas resueltas por
escrito), guion del turno de la sucursal, sistema de diseño único, y mocks de HUD del
turno, los 4 tipos de evento, cierre de turno, Taller (carga + brief + editor), vista de
admin, árbol de habilidades y modo sensible.

**Definition of Done del MVP 1**: la demo encadena Taller → partida → admin en un solo
recorrido de menos de 12 minutos, sin necesidad de explicar nada que no esté en pantalla.

### MVP 2 — El turno jugable de verdad (Sprint 2, 206 hs, 11 PBIs)

Se construye lo que el MVP 1 mostró mockeado, empezando por el juego. Épica A completa
(eventos que llegan solos, acciones con duración real, medidores que decaen,
consecuencias diferidas, score y récord) sobre un esqueleto técnico mínimo: repo con
docker-compose, modelo de datos, contrato de API y persistencia del progreso.

Cierra con el **test con 5-10 personas reales** (bache B2). La métrica no es si les
gustó: es cuántas volvieron a jugar sin que se lo pidiéramos.

### MVP 3 — El Taller productivo (Sprint 3, 210 hs, 10 PBIs)

La otra mitad del producto deja de ser una demo: carga real de documentos, RAG con
pgvector, clasificador de tipo, alerta de sensibilidad con marcado manual, generación del
contenido del turno con IA, flujo de aprobación con revisor especializado, auth y
multi-tenant. El runtime pasa a consumir las misiones publicadas desde el backend.

### MVP 4 — Admin, progresión y piloto (Sprint 4, 208 hs, 10 PBIs)

Vista de admin con datos reales de telemetría, comparativa primera vs. quinta partida,
modo sensible implementado en el runtime, árbol de habilidades, mundo con varios
escenarios, un segundo escenario creado solo con el Taller (la prueba de fuego de la
genericidad), el piloto real y el informe final.

## 4. Cobertura de los baches

| Bache | Se cierra en |
|---|---|
| B1 — el giro al turno no está construido | MVP 2 (PBIs 19 a 24) |
| B2 — nunca lo probó un usuario real | MVP 2 (PBI 26) y MVP 4 (PBI 44) |
| B3 — no hay forma de medir aprendizaje | MVP 3 (PBIs 33, 34) y MVP 4 (PBI 38) |
| B4 — modo sensible no implementado | MVP 4 (PBI 40) |
| B5 — clasificación automática de contenido | MVP 3 (PBI 28) |
| B6 — vista de admin | MVP 1 mockeada (12), MVP 4 real (37) |
| B7 — árbol de habilidades | MVP 1 mockeado (13), MVP 4 real (41) |
| B8 — mundo con varias misiones | MVP 4 (PBI 42) |
| T1 — no hay backend | MVP 2 (PBIs 16 a 18) |
| T2 — el RAG no existe | MVP 3 (PBI 27) |
| T3 — no hay persistencia real | MVP 2 (PBI 25) |
| T4 — no hay multi-tenant ni auth | MVP 3 (PBI 35) |
| T5 — no hay modelo de datos SQL | MVP 2 (PBI 17) |
| T6 — no hay contrato de API | MVP 2 (PBI 18) |
| T7 — no existe el repo con docker-compose | MVP 2 (PBI 16) |

Los 15 baches del documento de producto quedan asignados a un MVP. Ninguno queda afuera.

## 5. Roles en el Sprint 1

En el MVP 1 no hay backend, así que los roles se corren hacia diseño y maquetado:

| Integrante | Foco en el Sprint 1 | Hs |
|---|---|---|
| Dev 1 | HUD del turno y mock de ronda/procedimiento | 28 |
| Dev 2 | Mock de diálogo, cierre de turno y presentación | 32 |
| Dev 3 | Guion del turno y mock de auditoría | 32 |
| Dev 4 | Sistema de diseño, árbol de habilidades y revisiones de UX | 29 |
| Dev 5 | Mock de crisis y Taller de misiones | 32 |
| Dev 6 | Editor de misión y vista de admin | 31 |
| Dev 7 | Definición de producto, modo sensible y documentación | 30 |

Nadie queda por encima de las 32 hs contra una capacidad individual de 36. Los nombres
son placeholders: hay que reemplazarlos por los reales antes de entregar.

## 6. Definition of Done (transversal)

Una tarea está terminada cuando:

1. Cumple los 5 no negociables de la sección 3 del documento de producto.
2. Tiene el "cómo probarlo" del PBI ejecutado y documentado.
3. Usa el sistema de diseño (nada de estilos sueltos por pantalla).
4. En los MVPs 2 a 4: está mergeada en la rama principal y levanta con `docker compose up`.
5. Está en la demo del MVP, no solo en el repo.

## 7. Lo que falta definir antes del miércoles

- [ ] **Nombres reales** en lugar de Dev 1 a Dev 7, en la hoja Capacidad y en la pila del Sprint 1.
- [ ] **Confirmar las 14 hs semanales** con cada uno: si alguien tiene menos, se ajusta su fila y la carga se redistribuye.
- [ ] **Quién hace de Scrum Master y quién de Product Owner** del equipo.
- [ ] Si la cátedra pide **puntos de historia** además de horas (hoy está todo en horas, como el ejemplo del template).
- [ ] Si el Sprint 1 arranca el **24/09** o se corre al lunes 28/09 (correrlo obliga a recortar ~60 hs del MVP 1 o a comerse el buffer del final).
