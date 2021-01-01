<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode"> Stored Resources </base-button>
    <base-button @click="setSelectedTab('add-resources')" :mode="addResButtonMode"> Add Resources </base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
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
      addResource: this.addResource,
      deleteResource: this.deleteResource,
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
    },
    addResource(title, desc, url) {
      const NewResource = {
        id: new Date().toISOString(),
        title: title,
        description: desc,
        link: url
      };
      this.storedResourses.push(NewResource);
      this.selectedTab = 'stored-resources';
    },
    deleteResource(resId) {
      const resIndex = this.storedResourses.findIndex( res => res.id == resId );
      this.storedResourses.splice( resIndex , 1 );
    },
  },
}
</script>