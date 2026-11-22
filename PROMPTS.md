## Prompt 1 — LazyColumn y Pull-to-Refresh (Gemini en Android Studio)

**Fecha:** [COMPLETAR]

**Origen del prompt:** redactado con ayuda de Claude y ejecutado por el equipo en Gemini dentro de Android Studio.

**Prompt enviado:**

> Tengo un `LazyColumn` en Jetpack Compose que muestra una lista de `Episode` (id, title, show, durationSeconds). Optimizalo usando `key` y `contentType`, y envolvelo en `PullToRefreshBox` con un `isRefreshing` que viene de un `StateFlow` en el ViewModel. Explica por qué evita recomposiciones innecesarias.

**Respuesta de Gemini (resumen):** [COMPLETAR: qué código y qué explicación devolvió]

**Qué ajustó el equipo:** [COMPLETAR: qué se cambió o se descartó de la respuesta]

**Resultado en el proyecto:** en `HomeScreen.kt`, el `LazyColumn` va dentro de un `PullToRefreshBox` cuyo `isRefreshing` sale de `uiState.isRefreshing`, estado que expone `HomeViewModel` mediante `StateFlow`. Las listas de episodios usan `key = { it.id }`. El código final no aplica `contentType`. [COMPLETAR: indicar si fue una decisión del equipo o si se agregó después]

---

## Prompt 2 — Arquitectura inicial y plan de construcción (Claude)

**Fecha:** 2026-10-29

**Pedido del equipo (extracto):**

> Necesito diseñar una app en Android Studio con el lenguaje de programación Kotlin y Jetpack y tengo pautas que cumplir. [...] Te podrías convertir en un desarrollador de App profesional tanto en backend y frontend para asistirme en este proyecto. (Se adjuntó el texto del Caso de Requerimiento #2.)

**Respuesta (resumen):** interpretación de las cuatro pautas del caso, arquitectura MVVM (modelos, repositorio, `ViewModel` con `StateFlow`), un ejemplo de JSON ficticio, un orden de construcción en ocho pasos y el prompt usado en el Prompt 1.

**Qué ajustó el equipo:** el JSON de ejemplo de esa respuesta no es el definitivo. El proyecto usa `data.json` con las colecciones `categories`, `podcasts`, `episodes` y `liveStreams`. [COMPLETAR: otras decisiones propias del equipo]

---

## Prompt 3 — Maqueta visual inicial (Claude)

**Fecha:** 2026-10-29

**Pedido del equipo:**

> Pero presentame la app

**Respuesta (resumen):** maqueta con pantalla de inicio, buscador, mini reproductor y detalle del episodio. La versión tablet no se terminó.

**Qué ajustó el equipo:** [COMPLETAR: si esta maqueta se usó, se actualizó o se reemplazó por otra]

---

## Prompt 4 — Medir y simplificar el código (Claude)

**Fecha:** 2026-11-13

**Pedido del equipo:**

> Quiero ver si el código es muy extenso y no se puede sintetizar más. ¿Cómo hago para ver eso y, si es así, vos podés tratar de hacerlo? Como un profesional en esto.

**Respuesta (resumen):** explicación de cómo medir el tamaño del código en Android Studio y una propuesta de seis archivos simplificados (`StreamflowApp`, los cuatro `ViewModel` y la factory), de 924 a 693 líneas. Los cambios principales: eliminar estado duplicado en `PlayerViewModel`, concentrar el filtrado en un solo lugar en `HomeViewModel` y `SearchViewModel`, y evitar la repetición entre el diseño de celular y el de tablet.

**Qué ajustó el equipo:** [COMPLETAR: qué cambios se aplicaron, cuáles no, y cómo se verificó que la app siguiera funcionando]

---

## Prompt 5 — Revisión del brief contra el código (Claude)

**Fecha:** 2026-11-18

**Pedido del equipo:**

> Decime si esto está bien (se adjuntó el PDF del brief de producto y QA UX/UI).

**Respuesta (resumen):** se comparó el brief con el código y se detectaron afirmaciones que no coincidían con la app: la reproducción es simulada, la velocidad solo cambia la etiqueta, las transmisiones en vivo no se reproducen, la pantalla de inicio muestra un solo episodio destacado, los chips filtran por categoría y no por etiqueta, el tema usa Material 3 estándar, el botón Atrás en el detalle cierra la app y el "Me gusta" no se conserva.

**Qué ajustó el equipo:** [COMPLETAR: qué correcciones se hicieron al brief o al código]
