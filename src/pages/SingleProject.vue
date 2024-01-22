<template>
    <main class="container text-white" v-if="project">
        <h1>
            {{ project.title }}
        </h1>
        <p>{{ project.body }}</p>
        <div class="mb-3">
            <h4>Github:</h4>
            <a class="text-white" :href="project.url">{{ project.title }}</a>
        </div>
        <div class="mb-3">
            <h4>Technologies:</h4>
            <div class="d-flex">
                <div class="my-square me-3" v-for="technology in project.technologies">
                    <img :src="technology.image" :alt="technology.name">
                </div>
            </div>
        </div>
        <div>
            <h4>Category:</h4>
            <p>{{ project.category.name }}</p>
        </div>
        <div>
            <img class="img-fluid" :src="store.imgPath + project.image" :alt="project.title">
        </div>
    </main>
    <NotFound v-else></NotFound>
</template>

<script>
import axios from 'axios';
import { store } from '../store.js';
import NotFound from './NotFound.vue';
export default {
    name: 'SingleProject',
    data() {
        return {
            store,
            project: null
        }
    },
    components: {
        NotFound
    },
    methods: {
        getProjectData() {
            axios.get(this.store.apiUrl + "projects/" + this.$route.params.slug).then((res) => {
                if (res.data.results) {
                    this.project = res.data.results
                }

            })
        }
    },
    created() {
        this.getProjectData()
    }
}
</script>

<style lang="scss" scoped>
.my-square {
    width: 50px;
    height: 50px;
}
</style>