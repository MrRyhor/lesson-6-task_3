<template>
    <mail-input v-model:mail.check="mailVal" />    
</template>

<script>
import MailInput from './components/MailInput.vue'

export default {
    name: 'App',
    components: { MailInput },

    data() {
        return {
            mailVal: null,            
        }
    },
}
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
