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