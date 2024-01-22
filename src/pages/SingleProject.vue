<template>
    <main class="container">
        <h1 v-if="project">
            {{ project.title }}
        </h1>
        <div>
            <img class="img-fluid" v-if="project" :src="store.imgPath + project.image" :alt="project.title">
            <router-link :to="{ name: 'project:slug', params: { slug: project.slug } }">{{ project.title }}</router-link>
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import { store } from '../store.js';
export default {
    name: 'SingleProject',
    data() {
        return {
            store,
            project: null
        }
    },
    methods: {
        getProjectData() {
            axios.get(this.store.apiUrl + "projects/" + this.$route.params.slug).then((res) => {
                this.project = res.data.results;
            })
        }
    },
    created() {
        this.getProjectData()
    }
}
</script>

<style lang="scss" scoped></style>