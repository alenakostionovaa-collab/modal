<script setup>
import Parent from './components/Parent.vue';
import Child from './components/Child.vue';
import { shallowRef, ref } from 'vue';
const selected = ref(null);

const newSer =shallowRef(Child)
const newPhoto =ref([
  'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSpvlosglQHk3iKpZ4U38UZIPPlyirHLW4yZA&s',
  'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQriVaqlak5Dm5liVCZ5Vy6j5GPFTfrIT_gUg&s',
  'https://www.shutterstock.com/image-photo/foamy-blue-soothing-sea-waves-260nw-2711748115.jpg',

])

const selects = (photo) => {
selected.value = photo
isOpen.value = true
}

import Modal from './components/BaseModal.vue'
const isOpen = ref(false)

</script>

<template>
<img  v-for="(photo,id) in  newPhoto" :src="photo" :key="id"  @click="selects(photo)">
    <button  @click="isOpen = true">Открыть модалку</button>
  <Modal  :mass="selected" :show="isOpen" @close="isOpen = false">
    <h2>Внимание!</h2>
      <p>Здесь может быть форма или лог сервера.</p>
  </Modal>
  <button
  @click="newSer=(newSer === Parent ? Child : Parent)" >
  new slide
  {{ newSer === Parent ? 'Child' : 'Parent' }}
  </button>
  <component :is="newSer"/>
</template>
