<template>
    <nav class="page-nav">
        <ul class="page-nav__list">
            <li class="page-nav__item" v-for="page in totalPages" :key="page">
                <a href="#" class="page-nav__link" @click="handleEmitPage(page)">{{page}}</a>
            </li>
        </ul>
    </nav>
</template>

<script>
export default {
    props:{
        totalPages: {
            type: Number,
            required: true,
            },
    },
    data() {
        return {
          
        }
    },
    methods: {
        handleEmitPage(currentPage){
            console.log(currentPage);
            this.$emit('get-page-number', currentPage);
        }
    },
}
</script>

<style>

</style>