<template>
  <the-header :title="title"></the-header>
  <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import StoredResources from './components/learning-resources/StoredResources.vue'; 
import TheHeader from './components/layouts/TheHeader.vue';

export default {
  components: {
    StoredResources,
    TheHeader
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
      ],
      title: 'Remember Me'
    };
  }
}
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