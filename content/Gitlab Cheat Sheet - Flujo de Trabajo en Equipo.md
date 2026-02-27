

# 🚀 Configuración Inicial (Una sola vez)

- Clonar el repositorio

``` bash
	git clone <url-del-repositorio>
	cd <nombre-del-repositorio>
```

- Configurar tu identidad

``` bash
	git config user.name "Tu Nombre"
	git config user.email "tu@email.com"
```

# 📋 [[Git-Flujo Diario de Trabajo]]

## 1. Antes de Empezar a Trabajar

- Actualizar tu rama principal

``` bash
	git checkout main  # o master
	git pull origin main
```

- Crear una nueva rama para tu tarea

``` bash
	git checkout -b qa/nombre-descriptivo
```

## 2. Mientras Trabajas

- Ver estado de archivos modificados.[[Git-Estados de Git]]

``` bash
	git status
```

- Añadir cambios al staging

``` bash
	git add .                    # Todos los archivos
	git add archivo.txt          # Archivo específico
```

- Hacer commit

``` bash
	git commit -m "Descripción clara del cambio"
```

- Ver historial

``` bash
	git log --oneline
```

## 3. Sincronizar con la Nube

- Subir tu rama por primera vez

``` bash
	git push -u origin feature/nombre-descriptivo
```

- Subir cambios adicionales

``` bash
	git push
```

## 4. Actualizar tu Rama con Cambios del Equipo

### Opción 1: Merge (recomendado para principiantes)

``` bash
	git checkout main
	git pull origin main
	git checkout feature/nombre-descriptivo
	git merge main
```
### Opción 2: Rebase (historial más limpio)

``` bash
	git checkout feature/nombre-descriptivo
	git pull origin main --rebase
```

# 5. Integrar tu Trabajo

### Crear Merge Request en GitLab (preferido)
### O merge local:

``` bash
	git checkout main
	git pull origin main
	git merge feature/nombre-descriptivo
	git push origin main
```
### Eliminar rama local

``` bash
	git branch -d feature/nombre-descriptivo
```

# 🛡️ Prevenir Conflictos

- Actualizar frecuentemente (varias veces al día)

``` bash
	git pull origin main --rebase
```

-  Antes de hacer push

``` bash
	git pull --rebase
```

- Commits pequeños y frecuentes

``` bash
	git commit -m "Mensaje específico"
```

- Comunicación con el equipo sobre archivos compartidos

# ⚠️ [[Git-Resolver Conflictos]]

## Cuando aparece un conflicto:

 1. Ver archivos en conflicto

``` bash
	git status
```

1. Abrir archivos marcados y buscar:

``` bash
	<<<<<<< HEAD
	Tu código
	=======
	Código del otro desarrollador
	>>>>>>> rama-origen
```

 2. Editar manualmente, eliminar marcadores y decidir qué mantener

 3. Marcar como resuelto

``` bash
	git add archivo-resuelto.txt
```

4. Continuar el merge/rebase

``` bash
	git rebase --continue  # Si estabas en rebase
	git commit             # Si estabas en merge
```

 5. Subir cambios

``` bash
	git push
```

## Si te equivocas:

- Abortar merge

``` bash
	git merge --abort
```

-  Abortar rebase

``` bash
	git rebase --abort
```

- Deshacer último commit (mantiene cambios)

``` bash
	git reset --soft HEAD~1
```

- Descartar cambios locales

``` bash
	git checkout -- archivo.txt
	git restore archivo.txt
```

# 🔧 Comandos Útiles

- Ver ramas

``` bash
	git branch -a
```

-  Cambiar de rama

``` bash
	git checkout nombre-rama
	git switch nombre-rama
```

- Ver diferencias

``` bash
	git diff
	git diff main..feature/mi-rama
```

- Guardar cambios temporalmente

``` bash
	git stash
	git stash pop
```

- Ver quién modificó cada línea
	
``` bash
	git blame archivo.txt
```

- Traer rama remota
	
``` bash
	git fetch origin
	git checkout -b nueva-rama origin/nueva-rama
```

# 📌 Mejores Prácticas

1. Commits atómicos: Un cambio lógico por commit
2. Mensajes descriptivos: "Fix: corrige validación de email en formulario"
3. Pull antes de Push: Siempre actualiza antes de subir
4. Ramas por funcionalidad: Una rama = una tarea
5. Code review: Usa Merge Requests para revisión de código

