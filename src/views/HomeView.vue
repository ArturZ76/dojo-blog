<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="hanldeClick">Click</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "HomeView",
  setup() {
    const p = ref(null);

    let name = "mario";
    let age = 50;
    const hanldeClick = () => {
      console.log(p, p.value);
      p.value.classList.add("test");
      p.value.textContent = 'Hello ninjas!'
    };
    return {
      name: name,
      age: age,
      hanldeClick,
      p,
    };
  },
};
</script>
