# Introducción

En esta sesión se abordó cómo manejar los conflictos en Git al trabajar de manera colaborativa. El propósito fue aprender a identificar, resolver y prevenir conflictos durante la integración de ramas, además de revisar buenas prácticas y ejemplos prácticos.

## Contenidos principales

### 1. Definición de conflicto en Git

Un conflicto ocurre cuando dos o más desarrolladores modifican las mismas líneas de un archivo en ramas diferentes.
Git no puede decidir automáticamente qué versión conservar, por lo que el programador debe resolverlo manualmente.
La estructura típica de un conflicto muestra bloques de código separados por indicadores (<<<<<<< HEAD, =======, >>>>>>> branch).

### 2. Ejemplo de conflicto

Se trabajó con un archivo README.md en dos ramas distintas (fix/readme y feature/authors).
Cada rama modificó la misma línea (el título y fecha).
Al hacer merge, Git marcó el conflicto y fue necesario decidir qué cambios conservar (unir las dos fechas o priorizar una).

### 3. Estrategias para resolver conflictos

Editar manualmente el archivo y eliminar las marcas de conflicto.
Tomar una de las versiones o fusionarlas en una nueva.
Confirmar el cambio con un nuevo commit de resolución.

### 4. Tips para prevenir conflictos

- Hacer git pull frecuentemente para mantener las ramas actualizadas.
- Crear commits pequeños y frecuentes que sean fáciles de revisar.
- Dividir el trabajo en ramas pequeñas con cambios atómicos.
- Mantener comunicación constante con el equipo sobre merges y despliegues.
- Usar herramientas de integración (GitHub, GitLab) para establecer permisos, pull requests obligatorios y validaciones automáticas.

### 5. Uso de reglas y flujos de trabajo

En GitHub se pueden definir protecciones de ramas (ej. no permitir pushes directos a main).
Los pull requests permiten revisiones por otros miembros antes de integrar.
Se mencionaron hooks de Git (pre-commit, pre-push) para validar código antes de integrarlo.

### 6. Ejercicio práctico guiado

- Creación de un repositorio desde cero.
- Generación de ramas (fix/readme, feature/authors).
- Modificación de archivos en paralelo.
- Simulación de un conflicto y su resolución manual.
- Subida de cambios al repositorio remoto con git push.
- Conclusiones y próximos pasos
- Los conflictos en Git son inevitables, pero se pueden gestionar con buenas prácticas.
- La clave está en la comunicación, la frecuencia de integración y el uso de ramas pequeñas.
- Se sugirió investigar y practicar el uso de hooks, protección de ramas y flujos de trabajo con pull requests.


### Ejercicio de conflictos

### 1. Crear un repositorio nuevo

```sh
mkdir git-ejercicios-conflictos
cd git-ejercicios-conflictos
```
#### Iniciar repositorio
```sh
# iniciar repositorio
git init
```
#### Crear un archivo Inicial
```sh
echo "# Proyecto Git - Conflictos" > README.md
git add README.md
git commit -m "Inicialización del repositorio con README"
```

### 2. Crear Ramas
```sh
# Rama para Correcciones
git checkout -b fix/readme

# Rama para nueva funcionalidad 
git checkout main
git checkout -b feature/authors
```
### 3. Modificar archivos en paralelo
#### 📌 En fix/readme, modifica el README:
```sh
git checkout fix/readme
echo "Este proyecto es una práctica de resolución de conflictos." >> README.md
git add README.md
git commit -m "Agrega descripción al README"
```
#### 📌 En feature/authors, modifica el mismo README pero en otra línea:
```sh
git checkout features/authors
echo "Autores: Carlos y Equipo." >> README.md
git add README.md
git commit -m "Agrega sección de autores al README"
```

### 4. Generar un Conflicto

#### 1 Cambia a main
```sh
git checkout main
```
#### 2 Une primero la rama fix/readme(no habrá conflictos todavía)
```sh
git merge fix/readme
```
#### 3 Ahora intenta unir feature/authors
```sh
git merge fix/authors
```
#### 👉 Aquí deberías ver un conflicto en README.md.

### 5. Resolver el conflicto

#### Abre el archivo README.md. Verás algo como:
```md 
#### Proyecto Git - Conflictos
<<<<<<< HEAD
Este proyecto es una práctica de resolución de conflictos.
=======
Autores: Carlos y Equipo.
>>>>>>> feature/authors
```
#### ✍️ Resuélvelo manualmente, dejando una versión final limpia. Ejemplo:
```md 
# Proyecto Git - Conflictos
Este proyecto es una práctica de resolución de conflictos.
Autores: Carlos y Equipo.
```
#### Después, marca como resuelto

```sh
git add README.md
git commit -m "Resuelve conflictos entre fix/readme y features/authors"
```

### 6 Subir al repositorio 

#### Primero crea un repositorio en GitHub (por ejemplo: git-ejercicio-conflictos).
#### Luego, enlaza y sube:

```sh
git remote add origin git@github.com:TU_USUARIO/git-ejercicio-conflictos.git
git push -u origin main
git push origin fix/readme
git push origin feature/authors
```


### Glosario breve

- Commit: Registro de cambios confirmados en un repositorio.
- Merge: Acción de unir dos ramas en una sola.
- Pull: Operación para traer los cambios más recientes de una rama remota.
- Stash: Herramienta para guardar temporalmente cambios sin hacer commit.
- Hook: Script que se ejecuta automáticamente en ciertos eventos de Git.




