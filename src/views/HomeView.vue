<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}</h3>
    <div>
      <button @click="decreaseCounter" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter" class="btn">+</button>
    </div>

    <div class="edit">
      <h4>Edit Counter title:</h4>
      <input type="text" v-model="counterData.title" />
    </div>
  </div>
</template>
<script setup>
import { reactive } from "vue";

const appTitle = "My Counter App";
// const counter = ref(0),
//   counterTitle = ref("My Counter");

const counterData = reactive({
  count: 0,
  title: "My Counter",
});

const increaseCounter = () => {
  counterData.count++;
};

const decreaseCounter = () => {
  counterData.count--;
};
</script>
<!--
<script>
import { ref } from 'vue'
export default {
  setup() {
    const counter = ref(0)
    const increaseCounter = () => {
      counter.value++
    }
    const decreaseCounter = () => {
      counter.value--
    }
    return {
      counter,
      increaseCounter,
      decreaseCounter,
    }
  },
}
</script>
-->
<!--
<script>
export default {
  data() {
    return {
      counter: 0,
    }
  },
  methods: {
    increaseCounter() {
      this.counter++
    },
    decreaseCounter() {
      this.counter--
    },
  }
}
</script>
-->
<style scoped>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  padding: 10px;
  margin: 10px;
}
</style>
