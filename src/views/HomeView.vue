<script setup>
import { ref, computed } from 'vue'

// Estado reactivo (Reactividad)
const nuevaTarea = ref('')
const tareas = ref([
  { texto: 'Instalar Vue.js y Vite', completada: true },
  { texto: 'Configurar Router y Pinia', completada: true },
  { texto: 'Desplegar en Vercel', completada: false }
])

// Propiedad computada
const completadasCount = computed(() => {
  return tareas.value.filter(t => t.completada).length
})

// Métodos y manejo de eventos
const agregarTarea = () => {
  if (nuevaTarea.value.trim() !== '') {
    tareas.value.push({ texto: nuevaTarea.value, completada: false })
    nuevaTarea.value = ''
  }
}

const toggleTarea = (index) => {
  tareas.value[index].completada = !tareas.value[index].completada
}

const eliminarTarea = (index) => {
  tareas.value.splice(index, 1)
}
</script>

<template>
  <div style="min-height: 100vh; display: flex; align-items: center; justify-content: center; background-color: #1a1a1a; padding: 20px; box-sizing: border-box; width: 100%;">
    <main style="max-width: 500px; width: 100%; background: #242424; padding: 30px; border-radius: 12px; box-shadow: 0 8px 24px rgba(0,0,0,0.5); font-family: system-ui, sans-serif; color: #ffffff;">
      <h1 style="color: #42b883; text-align: center; margin-top: 0; font-size: 1.8rem;">⚡ Mi Aplicación Vue.js</h1>
      <p style="text-align: center; color: #aaa; margin-bottom: 20px; font-size: 0.95rem;">
        Gestor de Tareas Interactivo
      </p>

      <div style="display: flex; gap: 10px; margin-bottom: 20px;">
        <input 
          v-model="nuevaTarea" 
          @keyup.enter="agregarTarea"
          placeholder="Escribe una nueva tarea..." 
          style="flex: 1; padding: 12px; border-radius: 6px; border: 1px solid #444; background: #1a1a1a; color: #fff; font-size: 1rem; outline: none;"
        />
        <button 
          @click="agregarTarea" 
          style="padding: 12px 20px; background: #42b883; border: none; border-radius: 6px; color: white; font-weight: bold; cursor: pointer; font-size: 1rem;">
          Agregar
        </button>
      </div>

      <p style="font-size: 0.9rem; color: #888; margin-bottom: 15px;">
        Completadas: <strong style="color: #42b883;">{{ completadasCount }}</strong> de <strong>{{ tareas.length }}</strong>
      </p>

      <ul style="list-style: none; padding: 0; margin: 0;">
        <li 
          v-for="(tarea, index) in tareas" 
          :key="index"
          style="display: flex; justify-content: space-between; align-items: center; padding: 12px 16px; background: #2d2d2d; margin-bottom: 10px; border-radius: 8px; border: 1px solid #3a3a3a;"
        >
          <span 
            @click="toggleTarea(index)" 
            :style="{ textDecoration: tarea.completada ? 'line-through' : 'none', cursor: 'pointer', color: tarea.completada ? '#777' : '#fff' }"
          >
            {{ tarea.completada ? '✅' : '📌' }} {{ tarea.texto }}
          </span>
          <button 
            @click="eliminarTarea(index)" 
            style="background: #ff5252; color: white; border: none; padding: 6px 10px; border-radius: 6px; cursor: pointer; font-weight: bold;">
            ✕
          </button>
        </li>
      </ul>
    </main>
  </div>
</template>