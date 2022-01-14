<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResourceBtn">Stored Resource</base-button>
    <base-button @click="setSelectedTab('add-resource')" :mode="addResourceBtn">Add Resource</base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue'; 
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'zaq098jhddb',
          title: 'Official Guide',
          description: 'This is Vue Js official description.',
          link: 'https://v3.vuejs.org/'
        },
        {
          id: 'sgssbvxg754sg',
          title: 'Google',
          description: 'This is a Google official page/',
          link: 'https://www.google.com/'
        }
      ]
    };
  },
  provide() {
    return { 
      resources: this.storedResources,
      addNewResource: this.addResource,
      deleteResource: this.removeResource
    };
  },
  computed: {
    storedResourceBtn() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResourceBtn() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResource(index) {
      const indx = this.storedResources.findIndex(res => res.id === index);
      this.storedResources.splice(indx, 1);
    }
  }
}
</script>