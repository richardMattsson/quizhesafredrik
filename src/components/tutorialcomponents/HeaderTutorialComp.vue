<script>
  import { mapStores } from 'pinia';
  import { useAuthStore } from '../../stores/useAuthStore';

  export default {
    props: {
      title: { type: String, default: 'Rubrik 1' },
      previousPage: { type: String, default: 'Föregående sida' },
      nextPage: { type: String, default: 'Nästa sida' },
      navigateBack: { type: String, default: '/tutorial/introduktion' },
      navigateForward: { type: String, default: '/tutorial/introduktion' }
    },
    computed: {
      ...mapStores(useAuthStore)
    }
  };
</script>
<template>
  <header class="container-color">
    <h1 class="tutorial-h1">{{ title }}</h1>
    <nav class="container-flex tutorial-nav">
      <router-link :to="navigateBack"
        ><button class="buttonDark">{{ previousPage }}</button></router-link
      >
      <section class="progress-bar">
        <progress
          v-if="authStore.currentUser"
          :value="authStore.currentUser.level ? authStore.currentUser.level : 0"
          :max="4"
        />
        <p v-if="authStore.currentUser">
          Genomfört
          {{ authStore.currentUser.level ? authStore.currentUser.level : 0 }} /
          4 övningar
        </p>
      </section>
      <router-link :to="navigateForward"
        ><button class="buttonDark">
          {{ nextPage }}
        </button></router-link
      >
    </nav>
  </header>
</template>

<style scoped>
  progress {
    width: 80%;
    border: 1px solid #333;

    border-radius: 5px;
  }
  progress::-webkit-progress-bar {
    background-color: #ddd;
  }
  progress::-webkit-progress-value {
    background-color: #333;
    border-radius: 5px;
  }
  progress::-moz-progress-bar {
    background-color: #333;
  }
  a > button {
    padding: 5px 5px;
  }
</style>
