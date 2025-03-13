<script>
  import QuestionComp from '../components/QuestionComp.vue';
  export default {
    components: {
      QuestionComp
    },

    data() {
      return {
        results: []
      };
    }
  };
</script>
<template>
  <!-- Frågan -->
  <QuestionComp :results="results" />
</template>

<style scoped></style>
