<script setup>
import { RouterLink, RouterView } from 'vue-router'




</script>

<template>
    
    <section class="text-gray-600 body-font">
        <div class="container px-5 py-8 mx-auto flex flex-wrap">
            <div class="flex flex-wrap -m-4">
                <div class="p-4 lg:w-1/2 md:w-full w-full" v-for="(jobPost, index) in ptJobPosts" :key="index">
                    <div class="flex border-2 rounded-lg border-gray-200 border-opacity-50 p-8 sm:flex-row flex-col">
                        <div class="flex-grow flex justify-between">
                            <h2 class="text-gray-900 text-lg title-font font-medium job-title" :class="jobPost.title" :id="jobPost.id">{{ jobPost.title }}</h2>
                            <a :href="jobPost.url" class="text-indigo-500 inline-flex items-center">See Job
                                
                            </a>
                        </div>
                    </div>
                </div>
                
            </div>
        </div>
    </section>
  
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
