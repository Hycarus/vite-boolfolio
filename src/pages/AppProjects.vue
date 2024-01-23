
<template>
    <div class="container ">
        <h1 class="my-5 text-white">Projects List</h1>
        <div class="row">
            <ProjectCard v-for="project in store.projects" :key="project.id" :project="project"></ProjectCard>
        </div>
    </div>
    <div class="text-center">
        <button class="btn btn-primary mx-2" @click="previousPage()" :disabled="currentPage == 1">Preovious</button>
        <button class="btn btn-primary mx-2" @click="nextPage()" :disabled="currentPage == lastPage">Next</button>
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
            store,
            currentPage: 1,
            lastPage: null,
            total: 0
        }
    },
    methods: {
        getAllProjects() {
            axios.get(this.store.apiUrl + "projects", { params: { page: this.currentPage } }).then((res) => {
                this.store.projects = res.data.results.data
                this.lastPage = res.data.results.last_page
                this.total = res.data.results.total
                this.currentPage = res.data.results.current_page
            })
        },
        previousPage() {
            if (this.currentPage > 1) {
                this.currentPage--
                this.getAllProjects()
            }
        },
        nextPage() {
            if (this.currentPage < this.lastPage) {
                this.currentPage++
                this.getAllProjects()
            }
        }
    },
    mounted() {
        this.getAllProjects()
    }

}
</script>

<style lang="scss" scoped></style>