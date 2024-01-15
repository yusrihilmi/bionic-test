<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import HeaderNavbar from './components/HeaderNavbar.vue'



</script>

<template>
    
    <HeaderNavbar />

    <!-- <ul>
      <li v-for="(jobPost, index) in ptJobPosts" :key="index">
        <h2>{{ jobPost.title }}</h2>
        <a :href="jobPost.url">See Job</a>
        
      </li>
    </ul> -->

    <!-- <RouterLink to="/about">About</RouterLink> -->
  
    
    

  <RouterView />
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      ptJobPosts: [],
    };
  },
  mounted() {
    this.fetchJobPosts();
  },
  methods: {
    fetchJobPosts() {
      axios.get('./data/bti.json')
        .then(response => {
          // Assuming the API response is an array of job posts
          this.ptJobPosts = response.data;
        })
        .catch(error => {
          // Handle errors here
          console.error('Error fetching data:', error);
        });
    },
  },
};
</script>
