<script setup>
import { ref } from 'vue'

// Reactividad
const nuevaTarea = ref('')
const tareas = ref([
  { texto: 'Instalar Vue.js y Vite', completada: true },
  { texto: 'Configurar Router y Pinia', completada: true },
  { texto: 'Desplegar en Vercel', completada: false }
])

// Manejo de eventos
const agregarTarea = () => {
  if (nuevaTarea.value.trim() !== '') {
    tareas.value.push({ texto: nuevaTarea.value, completada: false })
    nuevaTarea.value = ''
  }
}

const eliminarTarea = (index) => {
  tareas.value.splice(index, 1)
}
</script>

<template>
  <main style="max-width: 600px; margin: 40px auto; padding: 20px; font-family: sans-serif; color: #f2f2f2;">
    <h1 style="color: #42b883; text-align: center;">⚡ Mi Aplicación Vue.js</h1>
    <p style="text-align: center;">Demostración de Reactividad, Componentes y Eventos</p>

    <div style="display: flex; gap: 10px; margin-bottom: 20px;">
      <input 
        v-model="nuevaTarea" 
        @keyup.enter="agregarTarea"
        placeholder="Escribe una nueva tarea..." 
        style="flex: 1; padding: 10px; border-radius: 6px; border: 1px solid #444; background: #222; color: #fff;"
      />
      <button 
        @click="agregarTarea" 
        style="padding: 10px 20px; background: #42b883; border: none; border-radius: 6px; color: white; font-weight: bold; cursor: pointer;">
        Agregar
      </button>
    </div>

    <ul style="list-style: none; padding: 0;">
      <li 
        v-for="(tarea, index) in tareas" 
        :key="index"
        style="display: flex; justify-content: space-between; align-items: center; padding: 12px; background: #2a2a2a; margin-bottom: 8px; border-radius: 6px;"
      >
        <span 
          @click="tarea.completada = !tarea.completada" 
          :style="{ textDecoration: tarea.completada ? 'line-through' : 'none', cursor: 'pointer', color: tarea.completada ? '#888' : '#fff' }"
        >
          {{ tarea.completada ? '✅' : '📌' }} {{ tarea.texto }}
        </span>
        <button 
          @click="eliminarTarea(index)" 
          style="background: #ff5252; color: white; border: none; padding: 4px 8px; border-radius: 4px; cursor: pointer;">
          ✕
        </button>
      </li>
    </ul>
  </main>
</template>