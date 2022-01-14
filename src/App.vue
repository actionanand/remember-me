<template>
  <ul>
    <learning-resource v-for="res in storedResources" :key="res.id"
    :title="res.title" :description="res.description" :link="res.link"
    ></learning-resource>
  </ul>
</template>

<script>
import LearningResource from './components/learning-resources/LearningResource.vue';

export default {
  components: {
    LearningResource
  },
  data() {
    return {
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
  }
}
</script>