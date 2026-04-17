1. **Ventajas frente a otras alternativas:**
   - **Frente a cambiar de rama en el mismo directorio:** Evita tener que lidiar con `git stash` constantemente, guardar cambios de trabajo incompletos, la mezcla de node_modules (o dependencias equivalentes) que pueden volverse incompatibles, y permite tener el IDE abierto mostrando varias ramas simultáneamente de forma segura.
   - **Frente a clonar el repositorio varias veces:** No duplica todo el historial pesado en disco, sino que comparte la carpeta oculta `.git`. Además, es más rápido de crear, ocupa menos espacio en disco, y las ramas creadas en un directorio están inmediatamente disponibles en tu repositorio local global.

2. **Situaciones reales de uso:**
   - **Review de una Pull Request (PR) pesada:** Si un compañero necesita que revises un PR complejo que requiere arrancar la aplicación, puedes crear un worktree paralelo. Así lo revisas, haces pruebas de integración, y mantienes intacto tu entorno local de la tarea en la que estás actualmente trabajando sin tener que reconstruir dependencias.
   - **Probar un hotfix urgente:** Tienes cambios sin confirmar a mitad de desarrollo, pero surge un bug en producción que deber reparar de inmediato. En lugar de ensuciar tus cambios actuales o forzar commits temporales, añades un worktree apuntando a la rama `main` y arreglas el bug desde allí.

3. **Buenas prácticas para organizar y nombrar worktrees:**
   - **Nomenclatura coherente:** Nombrarlos con un prefijo indicativo del propósito como `wt-<nombre-feature>` o `worktree-<tema>`.
   - **Estructura separada del repo original:** Agrupar todos los worktrees siempre fuera de la misma raíz o sub-directorios para evitar la indexación por accidente en el repositorio principal (para esto se usa `../` o un directorio como `/tmp/worktrees/repo`).
   - **Mantenimiento periódico:** Limpiar los entornos que ya no necesites utilizando `git worktree remove` y hacer mantenimiento para liberar referencias fantasma usando `git worktree prune`.
