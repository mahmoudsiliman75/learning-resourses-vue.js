<template>
    <ul>
    <learning-resourse
      v-for="resourse in resources"
      :key="resourse.id"
      :title="resourse.title"
      :description="resourse.description"
      :link="resourse.link"
    ></learning-resourse>
  </ul>
</template>

<script>
import LearningResourse from './LearningResourse.vue';

export default {
  components: {
    'learning-resourse': LearningResourse,
  },
  inject: ['resources'],
}
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    margin: auto;
    max-width: 40rem;
  }
</style>