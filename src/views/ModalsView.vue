<template>
  <div class="modals">
    <h1>This is an modals page</h1>
    <button @click="showModal = true">Show modal</button>
    <Teleport to="body">
      <div 
        v-if="showModal"
        class="modal"
      >
        <h2>This is Modal</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Minima, blanditiis totam? Necessitatibus quibusdam, incidunt aut eum, atque eos veritatis placeat reiciendis velit asperiores voluptatibus? Autem quis quo ut omnis nam!</p>
        <button @click="showModal = false">Hide modal</button>
      </div>
    </Teleport>
  </div>
</template>
<script setup>
import { ref } from "vue";

const showModal = ref(false);

</script>
<style scoped>
.modal {
  background: beige;
  color: #333;
  padding: 10px;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
.modal button {
  margin: 10px 0px;
}
.modal h2 {
  border-bottom: 1px solid #eee;
  padding-bottom: 10px;
}
</style>