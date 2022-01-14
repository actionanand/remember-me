<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResourceBtn">Stored Resource</base-button>
    <base-button @click="setSelectedTab('add-resource')" :mode="addResourceBtn">Add Resource</base-button>
  </base-card>
  <component :is="selectedTab"></component>
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
    return { resources: this.storedResources };
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
    }
  }
}
</script>