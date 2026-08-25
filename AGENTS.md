# AGENTS.md

Repositorio público de datos de amiibo de GameWall: catálogo, compatibilidad e imágenes servidos mediante jsDelivr. El tooling que genera y publica estos datos vive en el repositorio privado `jfmargar/GameWallAmiiboSync`.

## Triaje e issues

- El Project de GitHub **Gamewall** (`https://github.com/users/jfmargar/projects/3`) es la fuente de verdad del triaje para este repo, la app, la web y el sincronizador.
- Antes de sugerir o empezar trabajo, consulta `gh project item-list 3 --owner jfmargar --format json`.
- Elige entre `Status = Ready`, por prioridad `P0`, `P1`, `P2`; `next` solo desempata. No empieces `Backlog` o `blocked` salvo elección explícita.
- Mantén el flujo habitual `Backlog → Ready → In progress → Done`: pasa a `In progress` al asignar/crear rama y a `Done` solo tras validar, subir la rama, fusionarla directamente con `--no-ff`, subir `main` y cerrar el issue. Usa `In review` únicamente cuando exista una PR o revisión explícita.
- Si el trabajo activo se bloquea temporalmente, conserva `In progress` y añade `blocked`; vuelve a `Backlog` solo si se detiene a la espera de una dependencia externa.
- Añade al Project cualquier issue o PR nuevo de este repo.

## Git

- Trabaja en una rama `feature/*` creada desde `main`; no commitees trabajo directamente en `main`.
- Tras validar, commitea y sube la rama, fusiónala directamente en `main` con `--no-ff`, sube `main` y solo entonces cierra el issue.
- Las PR son opcionales; créalas solo si el usuario pide revisión o la exige CI.

## Publicación

- Los tags publicados son inmutables; una corrección requiere un tag nuevo.
- No elimines datos o imágenes ya publicados: pueden seguir referenciados por colecciones existentes.
- Coordina cualquier cambio de formato o tag con `GameWallAmiiboSync`, la app y la web.
