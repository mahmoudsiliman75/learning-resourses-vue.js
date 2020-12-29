<template>
  <the-header title="Remember Me"></the-header>
  <stored-resources :resources="storedResourses"></stored-resources>
</template>

<script>
import StoredResources from './components/learning-resourses/StoredResources.vue';
import TheHeader from './components/layouts/TheHeader.vue';

export default {
  components: {
    'stored-resources': StoredResources,
    'the-header': TheHeader,
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

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

  * {
    box-sizing: border-box;
  }

  html {
    font-family: 'Roboto', sans-serif;
  }

  body {
    margin: 0;
  }
</style>