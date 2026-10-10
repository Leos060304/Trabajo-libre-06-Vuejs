# Aplicación Web Vue.js - Trabajo Libre 06

##  Descripción y Propósito
Esta aplicación es un **Gestor de Tareas Interactivo (To-Do List)** funcional desarrollado con **Vue.js 3** y **Vite**. Permite administrar tareas en tiempo real mediante una interfaz reactiva, moderna y adaptable.

---

##  Conceptos de Vue.js Aplicados

- **Reactividad (`ref` & `v-model`):** Sincronización bidireccional entre la entrada de texto del usuario y el estado interno.
- **Propiedades Computadas (`computed`):** Cálculo automático e instatáneo del número de tareas completadas frente al total.
- **Manejo de Eventos (`v-on` / `@`):**
  - `@click` y `@keyup.enter` para la creación de nuevas tareas.
  - `@click` para alternar el estado de completado/pendiente de cada tarea.
  - `@click` en el botón de eliminación para modificar el arreglo de datos.
- **Gestión de Componentes y Estado:** Estructura basada en Composition API (`<script setup>`) y Pinia/Router configurados en el proyecto.

---

##  Demostración en Vivo
 **URL de Producción:** https://trabajo-libre-06-vuejs-bm0adhabz-leos-enterprises.vercel.app

---

##  Instrucciones para Ejecución Local

Sigue estos pasos para clonar y ejecutar el proyecto en tu entorno local:

1. **Clonar el repositorio:**
   ```bash
   git clone [https://github.com/Leos060304/Trabajo-libre-06-Vuejs.git](https://github.com/Leos060304/Trabajo-libre-06-Vuejs.git)
   cd Trabajo-libre-06-Vuejs