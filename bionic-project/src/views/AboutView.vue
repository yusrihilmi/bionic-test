<script setup>
import { RouterLink, RouterView } from 'vue-router'




</script>

<template>
    
    <ul>
      <li v-for="(jobPost, index) in ptJobPosts" :key="index">
        <h2>{{ jobPost.title }}</h2>
        <a :href="jobPost.url">See Job</a>
        
      </li>
    </ul>
  
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
