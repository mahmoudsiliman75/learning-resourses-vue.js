<template>
  <ul v-for="resourse in storedResourses" :key="resourse.id"> 
    <li> <strong>ID:</strong> {{resourse.id}}  </li>
    <li> <strong> Title: </strong> {{resourse.title}} </li>
    <li> <strong> Description: </strong> {{resourse.description}} </li>
    <li> <strong> Llink: </strong> <a :href="resourse.link">{{resourse.link}}</a> </li> 
  </ul>
</template>

<script>
export default {
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
}
</script>