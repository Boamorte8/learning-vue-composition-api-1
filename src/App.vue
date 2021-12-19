<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
    <h3>{{ title }}</h3>
    <h3>{{ description }}</h3>
    <button @click="setAge">Change age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">Set Name</button>
      <!-- <input type="text" placeholder="Last Name" v-model="lastName" /> -->
      <!-- <input type="text" placeholder="First Name" @input="setFirstName" />
      <input type="text" placeholder="Last Name" @input="setLastName" /> -->
    </div>
  </section>
</template>

<script>
import { computed, reactive, ref, watch } from 'vue';

export default {
  setup() {
    // const userName = 'MaximilianR';
    // const userName = ref('Maximilian');
    const firstName = ref('');
    const lastName = ref('');
    const lastNameInput = ref(null);
    const age = ref(31);
    const user = reactive({
      name: 'Esteban',
      age: 30
    });
    const test = {
      title: ref('This is a title'),
      description: ref('This is a description')
    };

    const userName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    watch([age, userName], (newValues, oldValues) => {
      console.log('Age or username changed');
      // console.log('newValues', newValues);
      // console.log('oldValues', oldValues);
      console.log('Old age', oldValues[0]);
      console.log('New age', newValues[0]);
      console.log('Old username', oldValues[1]);
      console.log('New username', newValues[1]);
    });
    // watch(age, (newValue, oldValue) => {
    //   console.log('Age changed');
    //   console.log('newValue', newValue);
    //   console.log('oldValue', oldValue);
    // });

    // setTimeout(() => {
    //   userName.value = 'Max';
    //   user.name = 'Teban';
    //   test.title.value = 'This is a new title';
    // }, 8000);

    const setAge = () => {
      age.value = age.value + 1;
    };

    const setFirstName = (e) => {
      firstName.value = e.target.value;
    };

    // const setLastName = (e) => {
    const setLastName = () => {
      // lastName.value = e.target.value;
      // lastName.value = this.$refs.lastNameInput.value;
      lastName.value = lastNameInput.value.value;
    };

    return {
      userName,
      age,
      user,
      title: test.title,
      description: test.description,
      setAge,
      setFirstName,
      setLastName,
      firstName,
      lastName,
      lastNameInput,
    };
  },
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
  // methods: {
  //   setNewAge() {
  //     this.age = this.age + 1;
  //   }
  // },
  // watch: {
  //   age(newAge) {
  //     console.log(`Age changed to ${newAge}`);
  //   }
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