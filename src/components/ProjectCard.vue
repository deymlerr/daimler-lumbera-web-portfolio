<template>
    <div class="card col-md-3">
        <img :src="project.image" class="card-img-top p-2 img-fluid" alt="...">
        <div class="card-body d-flex flex-column">
        <h5 class="card-title text-center">{{project.title}}</h5>
        <p class="card-text flex-grow-1 d-flex align-items-center">
            {{project.description}}
        </p>
        <div class="d-flex justify-content-center gap-2 mt-auto">
            <button class="btn btn-primary d-inline">Live Demo</button>
            <button class="btn btn-primary d-inline">GitHub</button>
        </div>
        </div>
    </div>
</template>

<script setup>
    import {defineProps} from 'vue';

    defineProps({
        project: Object
    })
</script>