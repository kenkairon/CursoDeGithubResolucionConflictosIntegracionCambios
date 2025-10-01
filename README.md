# 🌀 Resolución de Conflictos en Git

Cuando trabajamos en equipo con **Git y GitHub**, es común que se produzcan conflictos al combinar ramas.  
Un **conflicto** ocurre cuando Git no puede decidir automáticamente qué cambios mantener porque dos o más personas han modificado la misma parte del código.

---

## 📌 ¿Qué es un Conflicto?

Un conflicto se genera cuando:
- Dos ramas modifican la misma línea de un archivo.
- Un archivo fue editado en una rama y eliminado en otra.
- Existen diferencias irreconciliables que Git no puede resolver por sí solo.

En estos casos, **Git requiere intervención humana** para decidir qué cambios conservar.

---

## 📖 Estructura del Conflicto

Cuando ocurre un conflicto, Git marca la sección problemática en el archivo:

```text
<<<<<<< HEAD
= link
=======
= link_to
>>>>>>> main



