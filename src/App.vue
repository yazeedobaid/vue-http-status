<template>
<http-status-page :statusCode="statusCode" :statusMessage="statusMessage">
</http-status-page>
</template>

<script>
import httpStatusPage from "./components/httpStatusPage.vue";
export default {
    name: "App",
    components: {
        "http-status-page": httpStatusPage
    },
    data() {
        return {
            statusCode: 201,
            statusMessage: "Successfully Processed!"
        }
    }
};
</script>

<style lang="scss">

</style>
