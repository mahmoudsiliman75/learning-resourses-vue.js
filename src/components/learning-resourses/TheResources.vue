<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode"> Stored Resources </base-button>
    <base-button @click="setSelectedTab('add-resources')" :mode="addResButtonMode"> Add Resources </base-button>
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResources from './AddResources.vue';

export default {
  components: {
    'stored-resources': StoredResources,
    'add-resources': AddResources,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
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
  provide() {
    return {
      resources: this.storedResourses,
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab == 'stored-resources' ? null : 'flat' 
    },
    addResButtonMode() {
      return this.selectedTab == 'add-resources' ? null : 'flat'
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    }
  },
}
</script>