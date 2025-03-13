<script>
  import { RouterLink } from 'vue-router';
  import { useAuthStore } from '../stores/useAuthStore';

  export default {
    data() {
      return {
        authStore: useAuthStore()
      };
    },
    computed: {
      currentUser() {
        return this.authStore.currentUser;
      }
    }
  };
</script>
<template>
  <nav>
    <a
      v-if="currentUser"
      class="nav-links"
      href="#"
      @click.prevent="authStore.logout()"
      >Logga ut</a
    >
    <a v-else class="nav-links" href="#/login">Logga in</a>
    <RouterLink class="nav-links" to="/tutorial/introduktion"
      >Övningar</RouterLink
    >
    <RouterLink class="nav-links" to="/">Hem</RouterLink>

    <RouterLink class="nav-links" to="/scoretable">Highscore</RouterLink>

    <RouterLink class="nav-links" to="/information">Länkar</RouterLink>
  </nav>
</template>

<style scoped>
  nav {
    display: flex;
    justify-content: center;

    align-items: center;
    position: sticky;
    width: 100%;
    height: 50px;
    padding: 0.5rem 0;
    background-color: #333;
    color: whitesmoke;
    margin: 0;
    padding: 0;

    justify-content: space-around;
  }

  .nav-links {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;

    font-size: 1rem;
    border-right: 1px solid rgb(139, 139, 139);
    text-align: center;
  }

  .nav-links:hover {
    cursor: pointer;
    background-color: #555;
  }

  @media screen and (min-width: 470px) {
    nav {
      display: flex;
      justify-content: center;

      align-items: center;
      position: fixed;
      top: 0;
      /* left: 0;
      right: 0; */
      bottom: 0;
      width: 100%;
      height: 50px;
      padding: 0.5rem 0;
      background-color: #333;
      color: whitesmoke;
      margin: 0;
      padding: 0;

      justify-content: space-around;
    }
  }
</style>
