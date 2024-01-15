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

    <section class="text-gray-600 body-font relative">
        <div class="container px-5 py-6 mx-auto">
            <div class="flex flex-col text-center w-full mb-12">
                <div v-for="(jobDesc, index) in ptJobDescs" :key="index">
                    <h1 class="job-title-description text-left sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900"
                        :class="jobDesc.title" :id="jobDesc.id">{{ jobDesc.title }}</h1>
                    <p class="text-left leading-relaxed text-base job-description" :class="jobDesc.title"
                        v-html="jobDesc.description.txt"></p>
                </div>


            </div>
            <form @submit.prevent="submitApplication">
                <div class="w-full mx-auto">
                    <div class="flex flex-wrap -m-2">


                        <div class="p-2 w-1/2">
                            <div class="relative">
                                <label for="displayName" class="leading-7 text-sm text-gray-600">Name</label>
                                <input type="text" v-model="formData.displayName" required
                                    class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                            </div>
                        </div>

                        <div class="p-2 w-1/2">
                            <div class="relative">
                                <label for="phone" class="leading-7 text-sm text-gray-600">Phone</label>
                                <input type="number" v-model="formData.phone" required
                                    class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                            </div>
                        </div>
                        <div class="p-2 w-1/2">
                            <div class="relative">
                                <label for="email" class="leading-7 text-sm text-gray-600">Email</label>
                                <input type="email" v-model="formData.email" required
                                    class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                            </div>
                        </div>
                        <div class="p-2 w-1/2">
                            <div class="relative">
                                <label for="message" class="leading-7 text-sm text-gray-600">Message</label>
                                <input type="text" v-model="formData.message" required
                                    class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                            </div>
                        </div>
                        <div class="p-2 md:w-1/4 w-1/2">
                            <div class="relative">
                                <label for="resume" class="leading-7 text-sm text-gray-600">Resume</label>
                                <input type="file" @change="handleFileChange" accept=".pdf, .doc, .docx"
                                    class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                            </div>
                        </div>
                        <div class="p-2 mt-4 w-full">
                            <button type="submit"
                                class="flex text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Send
                                Message</button>
                        </div>
                    </div>
                </div>

            </form>

        </div>
    </section>
</template>

<style>
.job-title-description.Marketing {
    display: block;
}

.job-title-description {
    display: none;
}

.job-description.Marketing {
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
            formData: {
                displayName: '',
                subject: 'Marketing Planner',
                email: '',
                phone: '',
                message: '',
                resume: null,
                ptJobApplyType: 'APPLICATION',
                isActive: 'false',
                //   ptJobPost: ''
            },
            ptJobPosts: [],
            ptJobDescs: [],
        };
    },
    mounted() {
        this.fetchJobPosts();
        this.fetchJobDescs();
    },
    methods: {
        handleFileChange(event) {
            this.formData.resume = event.target.files[0];
        },
        submitApplication() {
            console.log('Form Data:', this.formData);
            this.formData = '';
            alert('Application submitted successfully! Check Console Log');
        },

        fetchJobPosts() {
            axios.get('./data/bti.json')
                .then(response => {
                    this.ptJobPosts = response.data;
                })
                .catch(error => {
                    console.error('Error fetching data:', error);
                });
        },
        fetchJobDescs() {
            axios.get('./data/bti.json')
                .then(response => {
                    this.ptJobDescs = response.data;
                })
                .catch(error => {
                    console.error('Error fetching data:', error);
                });
        },
    },
};
</script>
