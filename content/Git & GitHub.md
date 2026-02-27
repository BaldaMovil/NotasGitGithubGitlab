## 🔧 Configuración Inicial

```bash
# Configura tu identidad (solo una vez)
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"

# Ver configuración actual
git config --list
```
## 🆕 Iniciar y Clonar Repos

```bash
# Iniciar repositorio local
git init

# Clonar un repo existente
git clone https://github.com/usuario/repositorio.git
```
## 📂 Estado y Cambios

``` bash
# Ver estado actual de archivos
git status            

# Añadir archivos al área de staging
git add archivo.txt

# Agrega todo
git add *    

# Confirmar (commit) cambios
git commit -m "Mensaje claro del cambio"
```
## 🧭 Historial y Revisión

```bash
# Ver historial de commits
git log
git log --oneline --graph --all --decorate   # Visual bonito

# Ver diferencias
git diff                   # Cambios no stagueados
git diff --staged          # Cambios ya en staging
```
## 🔁 Branching y Merging

```bash
# Crear nueva rama
git branch nueva-rama

# Cambiar de rama
git checkout nueva-rama

# Crear y moverse a una rama
git checkout -b hotfix

# Fusionar ramas
git checkout main
git merge nombre-rama

# Eliminar rama
git branch -d nombre-rama
```
## 🌐 Conexión con GitHub

```bash
# Agregar repositorio remoto
git remote add origin https://github.com/usuario/repo.git

# Ver remotos
git remote -v
```
## 📤 Subir y Descargar

```bash
# Subir ramas al repositorio remoto
git push origin main
git push -u origin rama-nueva  # -u para recordar destino

# Descargar cambios
git pull
```
## 🔧 Stash, Reset y Revert

```bash
# Guardar cambios no confirmados (stash)
git stash
git stash list
git stash apply         # Recuperar último stash

# Resetear cambios
git reset archivo.txt          # Quitar de staging
git reset --hard HEAD          # Deshacer todo (peligroso)

# Revertir un commit
git revert <hash>
```
## ✅ Buenas Prácticas

- Commits pequeños y descriptivos: `"fix: corrige bug en login"`
- Evitar `commit -m "Cambios"` 🙅
- Usar `.gitignore` para excluir archivos innecesarios (ej: `node_modules/`, `.env`)
- Siempre hacer `pull` antes de `push`
- Crear ramas por feature: `feature/login`, `fix/404-error`

## 🧪 Comandos Avanzados

```bash
# Reescribir últimos commits (usa con cuidado)
git commit --amend

# Rebase para unificar historia
git rebase main

# Borrar archivos del historial
git rm archivo.txt
git commit -m "remove archivo"
```
## 📌 Alias útiles (opcional)

```bash
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.co checkout
git config --global alias.br branch
```
## 🗂️ Archivos clave

- `.gitignore` → Ignora archivos en el control de versiones
- `README.md` → Documentación visible en GitHub
- `LICENSE` → Tipo de licencia del proyecto

---

## 🤝 Flujo de Trabajo para Equipos (Pull Requests)

### 🧭 1. Clonar el repositorio remoto

```bash
git clone https://github.com/organizacion/repositorio.git
cd repositorio
```
### 🌱 2. Crear una rama para tu feature o fix

```bash
git checkout -b feature/nombre-claro
# Ejemplo: feature/formulario-login
```
### 🛠️ 3. Hacer cambios y confirmarlos

```bash
# Editás tus archivos
git add .
git commit -m "feat: agrega validación de email en formulario"
```
> 💡 Usa convenciones de commits como `feat`, `fix`, `docs`, `refactor`, etc. si tu equipo lo usa.

### 🔄 4. Sincronizar con main (opcional pero recomendable)

```bash
git checkout main
git pull origin main

git checkout feature/nombre-claro
git merge main
# o: git rebase main   # si tu equipo prefiere una historia lineal
```
### 🚀 5. Subir tu rama al remoto

```bash
git push -u origin feature/nombre-claro
```
### 📥 6. Abrir Pull Request en GitHub

1. Ir al repositorio en GitHub.
2. Verás un botón para crear un **Pull Request** (PR).
3. Asegurate de que la base sea `main` y compares con tu rama.
4. Agregá título claro y descripción detallada.

### 🧪 7. Revisar PRs de otros (Code Review)

- Usar los comentarios en línea.
- Aprobá si está listo o pedí cambios puntuales.
- Si es tuyo, corregí y hacé `push` a la misma rama para actualizar el PR.

### ✅ 8. Merge del PR

- Cuando todo esté aprobado y probado:
    - `Squash and merge` (sugerido para historia limpia).
    - O `Merge commit` si se necesita conservar el historial completo.

### 🧹 9. Eliminar la rama (opcional pero ordenado)

```bash
git branch -d feature/nombre-claro          # Local
git push origin --delete feature/nombre-claro  # Remoto
```
## 🚦Consejos para trabajo en equipo
- Siempre trabajá en ramas, **nunca en `main` directamente**.
- Hacé `pull` antes de empezar algo nuevo.
- Nombra tus ramas claramente: `feature/`, `bugfix/`, `hotfix/`, `docs/`.
- Comenta en los PRs para dejar contexto, no asumas que el código "se explica solo".
- Usá etiquetas de PR: `ready`, `in progress`, `needs review`, etc. si el equipo las tiene.