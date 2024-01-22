
<template>
    <div class="container ">
        <h1 class="my-5 text-white">Projects List</h1>
        <div class="row">
            <ProjectCard v-for="project in store.projects" :key="project.id" :project="project"></ProjectCard>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import { store } from '../store';
import ProjectCard from '../components/ProjectCard.vue';
export default {

    name: 'AppProjects',
    components: {
        ProjectCard
    },
    data() {
        return {
            store
        }
    },
    methods: {
        getAllProjects() {
            axios.get(this.store.apiUrl + "projects").then((res) => {
                this.store.projects = res.data.results.data
            })
        }
    },
    mounted() {
        this.getAllProjects()
    }

}
</script>

<style lang="scss" scoped></style>