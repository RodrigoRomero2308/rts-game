# Decisiones técnicas y alcance MVP — MESA CADENA

Documento vivo para **decisiones de implementación** y **límites de milestone** acordados en diseño/conversación. El pitch, pilares y vertical slice por sistemas siguen en `BRIEF_DISENO_MESA_CADENA.md`.

---

## Navegación, menús y sesión

- Los menús se entienden principalmente como **navegación** entre pantallas.
- **Guardado / carga (MVP):** lista de **archivos de partida** con **nombre editable** por el jugador; pueden existir **varias partidas del mismo mapa/escenario**.
- **Sin autoguardado** en esta fase; a futuro un **gestor de sesión** puede marcar partida “sucia”, pedir confirmación al salir, etc.

---

## Estado del juego (estructura mental)

- Separación estilo **backend / frontend** es válida: **reglas y estado** por un lado, **presentación e input** por otro; evitar **duplicar estado** entre capas.
- Preferencia explícita: el estado serializable y jugable sale de **unas pocas estructuras** (mapa, edificios, recursos globales del jugador, etc.), no de dispersar la verdad en muchos nodos.

---

## Escenarios y lista de niveles

- **Escenario:** mapa + objetivo + posibles twists (recurso/regla de layout).
- Una **partida** en ese mapa es una corrida normal; **no es obligatorio** tener UI de “lista de niveles” en el primer MVP (puede bastar **un flujo “Jugar”** hasta haber varios escenarios).

---

## Jugador vs asentamiento

- **Recursos “de ciudad”** asociados al asentamiento / mapa activo.
- **Datos del personaje / jugador:** dinero (u otra moneda macro), puntos de victoria, nombre; a futuro avatar u otros metadatos.
- Con **un solo asentamiento** en el mapa del MVP, población “global del jugador” y “del asentamiento” coinciden; si más adelante hay varios asentamientos, habrá que definir suma o reglas explícitas.

---

## Población (reglas acordadas)

- **Máximo por casa:** fijo según **tipo de edificio**.
- Al **bajar** la población por necesidades insatisfechas, **se va gente** (pueden quedar **plazas vacías** en las casas).
- **Cada nueva casa aporta +1** de población al colocarse; el **resto del cupo** se va llenando con el tiempo si las necesidades lo permiten.
- Partida nueva: población **0** hasta tener vivienda; luego la regla anterior aplica.

---

## Milestone: mapa y colocación (primer “done”)

**Considerado listo cuando:** el jugador puede **intentar colocar** un edificio y, si no es válido, recibir **rechazo con motivo** (cuando sea posible mostrarlo).

| Tema | Decisión |
|------|----------|
| Edificios | **Varias celdas** (footprint), no solo 1×1 |
| Terreno | Por ahora **tierra** y **agua** alrededor / en el mapa |
| Casilla inválida | **Ocupada**, alguna celda del footprint en **agua**, o **fuera del borde** del mapa (a futuro: elevación y otras reglas) |
| Feedback | **Motivo del rechazo** en lo posible; **preview/fantasma** no requerido en este milestone |
| Construcción | **Instantánea** |
| Demoler | **Otro milestone** (no bloquea el “done” de colocación anterior) |

---

## Próximos hitos (recordatorio, no compromiso de fecha)

- Demoler y recuperar celdas.
- Gestor de sesión + flujo guardar/cargar con confirmaciones.
- Preview de colocación si mejora UX.
- Reglas extra de validez (elevación, adyacencia a caminos, etc.) según diseño.

---

*Última actualización: decisiones consolidadas a partir de conversación de diseño técnico (mapa/colocación, estado, sesión, población).*
