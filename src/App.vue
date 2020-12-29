<template>
  <ul>
    <learning-resourse
      v-for="resourse in storedResourses"
      :key="resourse.id"
      :title="resourse.title"
      :description="resourse.description"
      :link="resourse.link"
    ></learning-resourse>
  </ul>
</template>

<script>
import LearningResourse from './components/learning-resourses/LearningResourse.vue';

export default {
  components: {
    'learning-resourse': LearningResourse,
  },
  data() {
    return {
      storedResourses: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official Vue.js Documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn To Google.....',
          link: 'https://google.com',
        },
      ],
    };
  },
};
</script>