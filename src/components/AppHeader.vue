<template>
    <div class="bg-dark">
        <nav class="navbar navbar-expand-lg  container">
            <div class="container-fluid">
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                    aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item" v-for="item in menu">
                            <router-link class="nav-link active text-white" :to="{ name: item.name }">{{ item.label
                            }}</router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>
export default {
    name: 'AppHeader',
    components: {

    },
    data() {
        return {
            menu: [
                {
                    label: 'Home',
                    name: 'home',
                },
                {
                    label: 'Projects',
                    name: 'projects',
                }
            ]
        }
    }
}
</script>

<style lang="scss" scoped></style>