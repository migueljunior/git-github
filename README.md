# Git y Github

## ¿Que son Git y Github?
- **Git =>** 
    - Software de control de versiones, solo guarda los cambios especificos.
    - Creador Linus Torvalds, es Open Source.
    - Anteriormente era un problema el trabajar en proyecdtos grandes, es un estandar actualmente muy usado.
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