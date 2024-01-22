<template>
    <main class="container" v-if="project">
        <h1>
            {{ project.title }}
        </h1>
        <div>
            <img class="img-fluid" :src="store.imgPath + project.image" :alt="project.title">
            <router-link :to="{ name: 'project:slug', params: { slug: project.slug } }">{{ project.title }}</router-link>
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

<style lang="scss" scoped></style>