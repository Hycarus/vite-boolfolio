<template>
    <router-link class="col-12 col-md-4 col-lg-3" :to="{ name: 'single-project', params: { slug: project.slug } }">
        <div class="card  d-flex justify-content-center align-items-center">
            <img class="img-fluid my-img" v-if="project" :src="store.imgPath + project.image" :alt="project.title">
            <div class="card-body">
                <h3>{{ project.title }}</h3>
            </div>
        </div>
    </router-link>
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

<style lang="scss" scoped>
.my-img {
    height: 350px;
    object-fit: contain;
}
</style>