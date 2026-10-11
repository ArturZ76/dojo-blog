<template>
  <div class="home">
    <h1>Home</h1>
    <!-- <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="hanldeClick">Click</button>
    <button @click="age++">add 1 to age</button>
    <input type="text" v-model="name" /> -->
    <!-- <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update ninja one</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update ninja two</button> -->
    <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      <p>{{ name }}</p>
    </div>
    <button @click="handleClick">Stop Watching</button>
  </div>
</template>

<script>
import { ref, computed, watch, watchEffect } from "vue";

export default {
  name: "HomeView",
  setup() {
    const search = ref('')
    const names = ref(['mario', 'luigi', 'yoshi', 'toad', 'bowser', 'koopa', 'peach'])

    //works always when value we put insde changes
    const stopWatch = watch(search, () => {
      console.log("Watch function run")
    })
    //work initialy and works everytime when value insode changes
    const stopEffect = watchEffect(() => {
      console.log("Watch Effect works", search.value)
    })

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    const handleClick = () => {
      stopWatch();
      stopEffect();
    }
    return { names, search, matchingNames, handleClick };
  },
  // setup() {
  //   const ninjaOne = ref({ name: "mario", age: 30 });
  //   const ninjaTwo = reactive({ name: "luigi", age: 35 });
  //   const updateNinjaOne = () => {
  //     ninjaOne.value.age = 40;
  //   };

  //   const updateNinjaTwo = () => {
  //     ninjaTwo.age = 50;
  //   };

  //   return { ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo };
  // },
  // setup() {
  //   //not reactive
  //   const p = ref(null);

  //   const name = ref("mario"); //use ref to make it reactive
  //   const age = ref(50);

  //   const hanldeClick = () => {
  //     (name.value = "luigi"), (age.value = 35);
  //   };
  //   return {
  //     name: name,
  //     age: age,
  //     hanldeClick,
  //     p,
  //   };
  // },
  data() {
    //standard reactive values
    return {
      score: 5,
    };
  },
};
</script>
