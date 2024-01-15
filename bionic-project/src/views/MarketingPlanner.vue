<script setup>
import { RouterLink, RouterView } from 'vue-router'




</script>

<template>
    
    <ul>
      <li v-for="(jobPost, index) in ptJobPosts" :key="index">
        <h2 class="job-title" :class="jobPost.title" :id="jobPost.id">{{ jobPost.title }}</h2>
        <a :href="jobPost.url">See Job</a>
        
      </li>
    </ul>

    <ul>
      <li v-for="(jobDesc, index) in ptJobDescs" :key="index">
        <h2 class="job-title-description" :class="jobDesc.title" :id="jobDesc.id">{{ jobDesc.title }}</h2>
        <div class="job-description" :class="jobDesc.title" v-html="jobDesc.description.txt"></div>
        
      </li>
    </ul>
  
</template>

<style>

.job-title-description.Marketing {
    display: none;
}

.job-title-description {
    display: none;
}

.job-description.Marketing  {
    display: block;
}

.job-description {
    display: none;
}

</style>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      ptJobPosts: [],
      ptJobDescs: [],
    };
  },
  mounted() {
    this.fetchJobPosts();
    this.fetchJobDescs();
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
    fetchJobDescs() {
      axios.get('./data/bti.json')
        .then(response => {
          // Assuming the API response is an array of job posts
          this.ptJobDescs = response.data;
        })
        .catch(error => {
          // Handle errors here
          console.error('Error fetching data:', error);
        });
    },
  },
};
</script>
