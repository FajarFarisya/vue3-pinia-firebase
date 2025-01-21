<template>
  <div class="home">
    <h2 ref="appTitleRef">{{ appTitle }}</h2>
    <h3>{{ counterData.title }}</h3>
    <div>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>

    <p>This counter is {{ addOrEven }}</p>

    <div class="edit">
      <h4>Edit Counter title:</h4>
      <input type="text" v-model="counterData.title" v-autofocus/>
    </div>
  </div>
</template>
<script setup>
import { computed, reactive, watch, onMounted, ref, nextTick } from "vue";
import { vAutofocus } from "@/directives/vAutofocus";

const appTitle = "My Counter App";
// const counter = ref(0),
//   counterTitle = ref("My Counter");

const counterData = reactive({
  count: 0,
  title: "My Counter",
});

const appTitleRef = ref(null);

// watcher
watch(() => counterData.count, (newCount) => {
  if (newCount === 20) {
    alert("Way to go! You made it to 20!");
  }
})

// computed
const addOrEven = computed(() => {
  if (counterData.count % 2 === 0)
  return "Even";
  else return "Odd";
});

const increaseCounter = async (amount) => {
  counterData.count += amount;
  await nextTick(() => {
    console.log("do something when the counter has updated in the DOM...");
  });
};

const decreaseCounter = amount => {
  counterData.count -= amount;
};

onMounted(() => {
  console.log(`The app title is: ${appTitleRef.value.offsetWidth} px wide!`);
});

// onBeforeUpdate(() => {
//   console.log("beforeUpdate");
// });
// onUpdated(() => {
//   console.log("updated");
// })
// onBeforeMount(() => {
//   console.log("beforeMount");
// })
// onMounted(() => {
//   console.log("mounted");
// });
// onBeforeUnmount(() => {
//   console.log("beforeUnmount");
// })
// onUnmounted(() => {
//   console.log("unmounted");
// })
// onActivated(() => {
//   console.log("activated");
// })
// onDeactivated(() => {
//   console.log("deactivated");
// })
</script>
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
