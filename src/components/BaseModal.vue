
// Modal.vue
<template>
  <teleport to="body">
    <div v-if="show" class="modal-overlay" @click.self="close">
      <div class="modal-content">
        <slot />
        <button @click="close">Закрыть</button>
         <img v-if="mass" :src="mass" />
      </div>
    </div>
  </teleport>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'
const props = defineProps({ show: Boolean, mass:String, })
const emit = defineEmits(['close'])
function close() { emit('close') }

</script>

<style scoped>
.modal-overlay {
  position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
  background: rgba(0,0,0,0.5); display: flex; align-items: center; justify-content: center;
  z-index: 9999;
}
.modal-content {
  background: #222; color: #fff; padding: 2rem; border-radius: 8px; min-width: 300px;
}
</style>
