<template>
    <div class="card col-12 col-md-4 col-lg-3">
        <img class="img-fluid" v-if="project" :src="store.imgPath + project.image" :alt="project.title">
        <router-link :to="{ name: 'single-project', params: { slug: project.slug } }"></router-link>
    </div>
</template>

<script>
import { store } from '../store.js';
export default {
    name: 'ProjectCard',
    props: ['project'],
    data() {
        return {
            store
        }
    },


}
</script>

<style lang="scss" scoped></style>