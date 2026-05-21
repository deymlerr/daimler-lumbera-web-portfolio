<template>
    <section class="container" id="projects">
        <h1 class="py-4">My Projects</h1>
        <div v-for="(group, index) in chunkedProjects" :key="index" class="row d-flex justify-content-center gap-5 pb-5">
            <ProjectCard v-for="project in group" :key="project.id" :project="project"/>
        </div>
    </section>
</template>

<script setup>
    import ProjectCard from './ProjectCard.vue';
    import {computed} from 'vue';
    import projects from '../data/projects.json'

    const chunkSize = 3;

    // This function is responsible for splitting the projects array into smaller arrays (chunks)
    const chunkedProjects = computed(() => {
        const chunks = [];

        for(let i=0; i < projects.length; i += chunkSize){
            chunks.push(projects.slice(i, i + chunkSize));
        }
        return chunks;
    })
</script>
