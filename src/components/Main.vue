<template lang="pug">
main.main
    MainContent()
    Week()
</template>
<script>
import MainContent from '@/components/MainContent.vue'
import Week from '@/components/Week.vue'
export default {
    components: {
        MainContent,
        Week
    }
}
</script>
<style lang="scss">
    
</style>