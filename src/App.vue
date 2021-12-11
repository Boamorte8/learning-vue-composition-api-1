<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
    <h3>{{ title }}</h3>
    <h3>{{ description }}</h3>
    <button @click="setAge">Change age</button>
  </section>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  setup() {
    // const userName = 'MaximilianR';
    const userName = ref('Maximilian');
    const age = ref(31);
    const user = reactive({
      name: 'Esteban',
      age: 30
    });
    const test = {
      title: ref('This is a title'),
      description: ref('This is a description')
    };

    // setTimeout(() => {
    //   userName.value = 'Max';
    //   user.name = 'Teban';
    //   test.title.value = 'This is a new title';
    // }, 8000);

    const setAge = () => {
      age.value = age.value + 1;
    };

    return {
      userName,
      age,
      user,
      title: test.title,
      description: test.description,
      setAge,
    };
  }
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>