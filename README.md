# Git y Github
## ¿Que son Git y Github?
- **Git =>** 
    - Software de control de versiones, solo guarda los cambios especificos.
    - Creador Linus Torvalds, es Open Source.
    - Anteriormente era un problema el trabajar en proyectos grandes, es un estandar actualmente muy usado.
    - Aumenta productividad y se utiliza a traves de la terminal.

## Configuracion Inicial de `git init` y `config`
```
// Confirmar version
git --version
// Iniciar Proyecto
git init
```
Esto inicia el proyecto y establece la rama **master** por defecto, es necesario actualizar la rama por defecto a **main** ya que este es el estandar actual.

Se lo realiza de la siguiente manera:
```
git config --global init.defaultBranch main
```

El comando de arriba configura por defecto que al usar `git init` se creara la rama **main**

Para ver la ayuda de git se utiliza el siguiente comando `git --help`

El flag `--global` aplica la configuracion de manera global en la computadora, dos parametros importantes son configurar el `usuario/nombre` y el `email`, se utiliza los siguientes comando:
```
git config --global user.name "<Nombre>"
git config --global user.email "<email>"
```

Para poder ver las configuraciones:
```
git config --list
// Ejemplo de Output
user.name=<name>
user.email=<email@gmail.com>
init.defaultbranch=main
```

## Comandos Basicos de Git: add, commit y log
El comando `git init` crea una carpte oculta con el nombre `.git` donde se guarda toda la informacion de los cambios realizados.
```
┌─(~/Workspace/git-github)───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────(leugim@terminator:pts/0)─┐
└─(17:32:07 on main ✹)──> ls -lha                                                                                                                                                        ──(Sat,Nov16)─┘
total 16K
drwxrwxr-x 3 leugim leugim 4.0K Nov 15 01:23 .
drwxrwxr-x 5 leugim leugim 4.0K Nov 15 01:23 ..
drwxrwxr-x 8 leugim leugim 4.0K Nov 16 17:30 .git
-rw-rw-r-- 1 leugim leugim 1.5K Nov 16 17:32 README.md
```

Cuando se realizan cambios se puede conocer el estado de los archivos con el comando `git status`
```
┌─(~/Workspace/git-github)───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────(leugim@terminator:pts/0)─┐
└─(17:32:12 on main ✹)──> git status                                                                                                                                                     ──(Sat,Nov16)─┘
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
Para agregar un archivo se utiliza el comando `git add <Archivo>` esto hace que el archivo entre a stage pero no agregado completamente "no comiteado".
```
┌─(~/Workspace/git-github)───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────(leugim@terminator:pts/0)─┐
└─(17:33:07 on main ✹)──> git add README.md                                                                                                                                              ──(Sat,Nov16)─┘
┌─(~/Workspace/git-github)───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────(leugim@terminator:pts/0)─┐
└─(17:45:32 on main ✹)──> git status                                                                                                                                                     ──(Sat,Nov16)─┘
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
```
Una manera grafica de verlo es la siguiente:
![Staging](./img/Staging.png)

Flujo de trabajo normal:
![Flujo de trabajo](./img/Flujo-de-trabajo.png)

Para sacarlo de staging se puede utilizar el comando `git rm --cached <Archivo>`
Para guardarlos en el repositorio despues que se encuentre en staging el comando es `git commit -m '<mensaje>'`

### Logs
Para ver la bitacora de los comandos `git log`
```
commit 22cba934950c50f24b49bff34dd764d47711747a (HEAD -> main)
Author: Junior <miguel.ajr89@gmail.com>
Date:   Sat Nov 16 18:00:26 2024 +0000

    Comandos agregados

commit d11b6912e05393e5aaa179be1946b689cce86a90
Author: Junior <miguel.ajr89@gmail.com>
Date:   Sat Nov 16 17:56:41 2024 +0000

    Agregados ejemplos de comandos e imagenes

commit b816250b44e6a849ba3ac15a9e5ac20226ef795c
Author: Junior <miguel.ajr89@gmail.com>
Date:   Sat Nov 16 17:30:55 2024 +0000

    Areglando subtitulos de clases

commit b8672592e208b0b3a9d5a46eafd57c9beaff351e (origin/main, origin/HEAD)
Author: Junior <miguel.ajr89@gmail.com>
Date:   Fri Nov 15 01:42:56 2024 +0000

    Agregando primeras notas

commit d081e382506f4bfdb5b4ec563f72535bd1f4e2a5
Author: Junior <miguel.ajr89@gmail.com>
Date:   Thu Nov 14 21:23:16 2024 -0400

    Initial commit
```
## Ramas y Fusión de Cambios: branch, merge, switch y checkout
### Ramas | Branches
El concepto de ramas es creo para poder trabajar de manera aislada a las demas personas:
![Ramas](./img/Branches.png)

Existen distintas manera de crear y cambiar ramas las cuales son:
- Para conocer en que rama uno se encuentra utiliza el comando `git branch`
- Para crear una nueva rama se utiliza el comando `git branch <Nombre rama>`
- Para cambiar a otra rama se utiliza el comando `git checkout <nombre rama a cambiar>`
- Para cambiar a otra rama se utiliza el comando `git switch <nombre rama a cambiar>`
- Para crear y cambiar a esa nueva rama se utiliza el comando `git checkout -b <nombre nueva rama>`
- Para crear y cambiar a esa nueva rama se utiliza el comando `git switch -b <nombre nueva rama>`
### Merge | Fusion
Para fusionar los cambios de una rama a otra es necesario utilizar el comando `git merge`. Supongamos que nos encontramos en la rama `main` y queremos fusionar los cambios de una rama individual con el nombre `rama-1`, entonces es necesario situarce en la rama `main` y ejecutar el comando `git merge rama-1` es decir indicar a la rama main que cambios de que rama se va a traer para fusionarlos.
### Eliminar o borrar una rama
Para eliminar una rama de manera local que no se utilizara mas se utiliza el comando `git branch -D <nombre rama a eliminar>`
## Volviendo en el Tiempo en Git: reset y revert
La diferencia entre ambos:
- `git reset` El comando reset te devuelve a un commit anterior, eliminando los cambios en el historial como si nunca hubieran ocurrido.
- `git revert` Crea un nuevo commit que "revierte" los cambios realizados por un commit especifico.

Manera de ejecutar los comandos:
- `git revert <id commit a revertir>` Se mostrara un mensaje del nuevo commit que se creara con el commit que se revirtio
- `git reset --hard <id commit a volver>` Se eliminaran los commits/historial hasta antes de este identificador.
- Se tienen 3 parametros importantes:
  - `soft` que permite eliminar los archivos
  - `mixed` que permite regresar los commits
  - `hard` permite deshacer todos los cambios **(esta es la ultima opcion a utilizar)**

Los problemas que resuelven:
- Correccion de errores
- Limpieza del historial
- Manejo de conflictos entre algunas ramas.