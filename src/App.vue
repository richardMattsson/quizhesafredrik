<script>
  import NavigationComp from './components/NavigationComp.vue';

  export default {
    components: { NavigationComp }
  };
</script>

<template>
  <main>
    <RouterView />
  </main>
  <NavigationComp />
</template>
