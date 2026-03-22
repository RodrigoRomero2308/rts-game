# Brief de diseño — **MESA CADENA** (título de trabajo)

**Código interno:** `[NOMBRE_CODIGO]` → **MESA CADENA** (working title)

## Rol y enfoque

Diseño como **game designer + product owner** de un estudio indie pequeño: refinar y concretar alcance sin expandir al estilo AAA. Prioridad: **loop jugable cerrado**, **claridad de pitch** y **factibilidad**.

---

## Contexto

Juego de **estrategia / city-builder económico** inspirado en la fantasía de **Anno 1404**: cadena de bienes, población con necesidades, comercio, crecimiento en **mapa acotado**, ritmo **pausado** y sensación de **orden y progreso**.

**No** es clonar Anno ni competir en escala con **Anno 1800** (multi-región, micromanagement imperial).

**Tesis de producto:** *“El corazón logístico de Anno en una sola mesa”.*

---

## Pitch

### Una línea (elevator)

> Una ciudad medieval en una sola isla donde cada granja, taller y camino importa: armá tu economía capa a capa en un solo mapa, sin administrar medio mundo.

### Párrafo corto (Steam-ready)

Gobernás un asentamiento en un territorio acotado: la gente necesita comer y vivir con dignidad, y vos decidís qué plantar, qué fabricar y por dónde circulan las mercancías. Las cadenas son cortas al principio y se enredan con el tiempo, pero siempre en el mismo lienzo: ves el cuello de botella, entendés el arreglo y sentís el alivio cuando el flujo vuelve a ordenarse. No hay imperio multi-región ni salto constante de mapa: el juego apuesta al **ritmo pausado**, al **progreso visible** y a la **claridad** de por qué algo falta o sobra. Si te gustó el corazón logístico de *Anno 1404* pero querés partidas más legibles, esto es tu mesa.

### Bullets tipo “Steam page” (5)

- **Un solo mapa, toda la economía:** población, producción y rutas en un único espacio legible.
- **Cadenas que crecen con vos:** de materias primas simples a bienes procesados, sin inflar la lista al estilo imperio global.
- **Población con necesidades claras:** el HUD explica qué falta y por qué afecta el ánimo o el crecimiento.
- **Layout que importa:** un recurso o condición del terreno empuja decisiones de dónde construir y cómo conectar almacenes y caminos.
- **Victoria o cierre de sesión en una corrida:** un objetivo único en el MVP (población / exportación / monumento / capítulo), con resumen de métricas al terminar.

---

## Público inicial (beachhead)

- Jugadores adultos con **nostalgia de Anno 1404** o interés en **logística + city-builder**.
- Buscan **partidas más legibles** que un imperio multi-mapa: **una isla / un valle**, menos saltos de contexto.
- **PC (Steam)**, valoran **demo**, toleran **early access** con roadmap claro si el core loop es sólido.

---

## Pilares de diseño (no negociables)

1. **Un solo mapa jugable** en el alcance inicial (sin colonias obligatorias en otro continente).
2. **Cadena económica legible:** pocas capas al inicio, con profundidad real (no cosmético).
3. **Progresión tangible:** la ciudad se ve distinta al subir la complejidad.
4. **Ritmo pausable / baja presión por defecto** (el combate, si existe, no secuestra el core).
5. **UI honesta:** si el jugador no entiende qué falta y por qué, el proyecto falla antes que el arte.

---

## Ideas de alcance inicial (MVP / vertical slice)

**Objetivo:** 2–4 horas de gameplay repetible y enseñable sin campaña épica.

### A. Loop mínimo económico

- Población con **1–2 necesidades** iniciales (ej. alimento + “comodidad básica”).
- **3–6 edificios** de producción encadenados (materia prima → procesado → consumo).
- Impuestos / ingreso simple que financie expansión.

### B. Mapa y espacio

- **Un bioma** dominante + **1 recurso o regla especial** del mapa (decisiones de layout).
- Rutas / almacenamiento con **cuellos de botella** interesantes pero no tediosos.

### C. Victoria o cierre de sesión (elegir UNA para el MVP)

- Objetivo por **población** / **producción exportada** / **monumento** / **capítulo** cerrado.
- Pantalla de resumen al terminar (métricas simples).

### D. Contenido narrativo

- **Mínimo viable:** tutorial integrado + misión corta opcional, o campaña de **3–5 objetivos** chicos.

### E. Riesgos a mantener chicos al inicio

- IA rival compleja, combate naval grande, diplomacia profunda, múltiples culturas jugables, procedural masivo.

---

## No-objetivos (primer entregable)

- [ ] Paridad de features con Anno moderno.
- [ ] Multijugador competitivo.
- [ ] Microtransacciones / economía F2P → asumir **premium** salvo decisión contraria con evidencia.

---

## 1. Sistemas priorizados — vertical slice (top 10) y dependencias

| # | Sistema | Depende de | Criterio “done” en gameplay |
|---|---------|------------|------------------------------|
| 1 | Mapa jugable + colocación de edificios | — | Colocás estructuras válidas; el juego rechaza o explica por qué no podés en un tile. |
| 2 | Población + viviendas | Mapa | Subís población al asignar casas; hay tope coherente con espacio/recursos. |
| 3 | Necesidades (1–2) | Población | Carencia visible; al satisfacerlas, mejora de estado visible (ánimo / crecimiento / paro). |
| 4 | Producción (3–6 edificios en cadena) | Mapa, recursos en tile si aplica | Entradas consumidas, salidas generadas; podés seguir un bien de origen a consumo. |
| 5 | Almacenamiento + rutas (abstractas) | Edificios | Sin almacén o ruta rota, la producción se atasca; al arreglarlo, el flujo se normaliza en pantalla. |
| 6 | Economía del jugador (impuestos / venta simple) | Población o producción | Ganás recurso “macro” y podés gastarlo en el siguiente eslabón. |
| 7 | Condición de victoria / fin de run (UNA) | Población o economía o monumento | Al cumplir, pantalla de resumen con 3–5 métricas. |
| 8 | Tutorial integrado + primer objetivo guiado | 1–6 | Jugador nuevo completa el loop sin documentación externa obligatoria. |
| 9 | UI de diagnóstico (“qué falta y por qué”) | Necesidades, producción, rutas | En menos de 30 s identificás el cuello principal desde la UI. |
| 10 | Guardado / carga (mínimo) | Estado del sim | Cerrás y reabrís; la ciudad sigue en el mismo estado. |

**Orden lógico de implementación:** 1 → 2 → 3 → 4 → 5 → 6 → (8 en paralelo desde el primer edificio) → 9 (pulido continuo) → 7 → 10.

---

## 2. User stories del tutorial hasta el primer “momento wow” económico

**Momento wow:** la primera vez que una **cadena completa corre sola** (materia prima → procesado → almacén → necesidad satisfecha o venta), con **feedback claro** en pantalla.

1. Como jugador, quiero colocar mi primer edificio de población para entender límites de terreno y validación.
2. Como jugador, quiero ver qué necesita mi gente (ej. alimento) en un solo panel.
3. Como jugador, quiero construir la fuente de materia prima enlazada al almacén o consumidor para ver el primer flujo entrante.
4. Como jugador, quiero construir el procesador (molino / cocina / taller) para transformar materia prima en bien usable.
5. Como jugador, quiero que el juego me avise si falta almacén o ruta para que el atasco sea enseñable.
6. Como jugador, quiero arreglar el cuello de botella y ver cómo se descongestiona la cola en la UI.
7. Como jugador, quiero recibir ingresos simples al estabilizar el bien para sentir que la economía “respira”.
8. Como jugador, quiero un objetivo corto opcional que cierre el slice con sensación de victoria pequeña.

**Checkpoint de wow:** al completar sobre todo la historia 6 (y 7 si aplica), el jugador puede articular: *“Ahora entiendo de qué vive mi ciudad.”*

---

## 3. Riesgos top 10 y mitigación

| # | Riesgo | Mitigación |
|---|--------|------------|
| 1 | Sobrediseño de cadena | MVP: 3–6 edificios fijos; backlog explícito; “done” = cadena trazable en UI. |
| 2 | Logística opaca | Panel de diagnóstico prioritario; playtests con observador externo por milestone. |
| 3 | Comparación tóxica con Anno | Pitch: “corazón logístico en una mesa”; no prometer paridad. |
| 4 | Alcance de mapa | Slice: mapa curado + 1 twist de recurso/layout. |
| 5 | Complejidad pathfinding / sim (1 dev) | Rutas abstractas edificio–edificio antes que multitudes animadas. |
| 6 | Sin condición de fin clara | Una sola victoria en scope S. |
| 7 | Tutorial largo | Tareas en el mundo; texto mínimo; tooltips donde haga falta. |
| 8 | Burnout del solo dev | Scope S estricto; hitos con build jugable; feature freeze del slice. |
| 9 | Mercado saturado | Nicho: nostalgia Anno + una isla legible; demo si encaja (ej. Steam Next Fest). |
| 10 | Deuda en guardado / estado | Modelo de datos simple desde el día 1; save/load temprano aunque sea básico. |

---

## 4. Variaciones de alcance: S, M, L

*(Los rangos tipo “8–12 semanas” son referencia humana de prototipo serio; el equipo ajusta según capacidad real.)*

### S — prototipo serio / vertical slice

- **Entra:** mapa fijo, 1 bioma + 1 recurso/regla de layout, 3–6 edificios, 1–2 necesidades, almacén + rutas abstractas, economía simple, **una** condición de victoria, tutorial mínimo, UI de diagnóstico usable, save/load básico, resumen de fin.
- **Fuera:** campaña larga, rival, combate, múltiples culturas, procedural grande, biomas extra, diplomacia, narrativa pesada.

### M — early access “core sólido”

- **Entra:** todo S + segunda capa de cadena (1–2 bienes más), segunda necesidad o variante estacional ligera, 3–5 misiones o capítulos cortos, más eventos de mapa, pulido UI/UX, **dos** condiciones de victoria acotadas.
- **Fuera:** multijugador, mapas infinitos, combate naval grande, IA rival compleja.

### L — visión de producto sin paridad AAA

- **Entra:** todo M + rival pasivo o comercio NPC simple, más edificios y layouts alternativos, modo escenario con 2–3 mapas curados, metaprogresión ligera si encaja con premium, audio/arte más production-ready.
- **Fuera:** paridad con *Anno 1800*, F2P, PvP competitivo serio.

---

## 5. Motores y decisión: arranque con **Godot**

Para un **solo desarrollador** con foco en simulación + UI + iteración rápida:

| Motor | Encaje | Ojo |
|-------|--------|-----|
| **Godot 4** | Gratis, 2D/isométrico ágil, GDScript o C#, buen flujo UI. | Sim pesada: optimizar o GDExtension (C++/Rust) si hace falta. |
| Unity | Mucho material grid/UI; C# maduro. | Revisar licencias según ingresos. |
| Unreal | Fuerte en 3D; Blueprints para prototipo. | Curva más alta si el foco es sim + UI. |

**Decisión del equipo:** comenzar el prototipo en **Godot 4** (versión estable actual del proyecto a documentar en `README` o en carpeta `godot/` cuando exista el proyecto).

### Próximos pasos técnicos sugeridos (Godot)

1. Crear proyecto Godot 4.x en el repo (carpeta `game/` o `mesa-cadena/`).
2. Definir **vista** inicial: 2D top-down o isométrico con grid; placeholder tiles.
3. Implementar **solo** sistema #1 del vertical slice (mapa + colocación) hasta criterio “done”.
4. Añadir `.godot/` a `.gitignore` si no está (cache local); versionar `project.godot` y escenas/scripts.

---

## Criterios de calidad (recordatorio)

- Si una feature no sirve al **loop de 2–4 h**, va fuera o a backlog explícito.
- Cada sistema debe tener **criterio de “done” observable en gameplay**, no solo en documento.

---

*Documento generado a partir del brief inicial del equipo; mantener sincronizado con decisiones de scope y con el roadmap de Godot.*
