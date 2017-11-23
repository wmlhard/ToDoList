<template lang="html">
    <div class="list-content">
        <list-header></list-header>
        <list-section></list-section>
        <list-footer></list-footer>
    </div>
</template>
<script>
    import listHeader from "./list-header.vue"
    import listSection from "./list-section.vue"
    import listFooter from "./list-footer.vue"
    export default {
        data(){
            return{
            }
        },
        components:{
            listHeader,
            listSection,
            listFooter

        },
        methods:{

        }
    }
</script>
<style lang="css">
    .list-content{
        background: #cdcdcd;
        width: 100vw;
        height: 100vh;
        overflow: hidden;
    }
</style>