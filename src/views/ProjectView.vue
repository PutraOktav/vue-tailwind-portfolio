<template>
    <p class="text-center mb-3 dark:text-blue-300">Projects from <font-awesome-icon icon="fa-brands fa-linkedin" /></p>
    <div class="max-h-[50vh] overflow-auto sm:w-4/12 mx-auto">
        <Loader v-if="loading" />
        <div v-if="error" class="text-red-500 text-center">{{ error }}</div>
        <div v-for="(project, index) in projects" :key="index">
            <a :href="project.url" target="_blank">
                <div class="bg-blue-300 mb-4 p-2 rounded-md shadow-md">
                    <h2 class="font-bold text-xl">{{ ++index }} {{ project.name }}</h2>
                    <p>{{ project.description }}</p>
                </div>
            </a>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Loader from '../components/Loader.vue';

const projects = ref([]);
const loading = ref(false);
const error = ref(null);

// Dummy data to simulate LinkedIn projects
const dummyProjects = [
    { name: 'Sistem Prediksi Modal dan Pakan Ikan', description: 'Jan 2021 - Present', url: 'https://aquatic.nokt.tech/' },
    { name: 'Web Migration from CodeIgniter (CI) to Laravel', description: 'Apr 2024 - Present', url: 'https://mesinumkm.com/' }
];

onMounted(async () => {
    try {
        loading.value = true;
        // Replace with actual LinkedIn data fetching if available
        projects.value = dummyProjects;
        loading.value = false;
    } catch (ex) {
        error.value = ex;
        loading.value = false;
    }
});
</script>
