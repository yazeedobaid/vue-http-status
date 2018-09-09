<template>
<div class="grid-container">

    <div class="status-data">
        <div class="status-data-code">
            {{ statusCode }}
        </div>
        <hr class="horizontal-divider">
        <div class="status-data-message">
            <p>{{ statusMessage }}</p>
        </div>
    </div>

    <div class="status-image">
        <img :src="getImgUrl(statusImage)" alt="status code image" srcset="">
    </div>

</div>
</template>

<script>
export default {
    name: "http-status-page",
    props: {
        statusCode: {
            type: Number,
            required: true
        },
        statusMessage: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            statusImage: null,
            statusImgPath: "../assets/"
        };
    },
    created() {
        switch (this.statusCode) {
            case 301:
                // Moved Permanently: This and all future requests should be directed to a given URL
                this.statusImage = "directions.svg";
                break;
            case 401:
                // Un-authorized access: No permissions to access the requisted resource
                this.statusImage = "warning.svg";
                break;
            case 403:
                // Forbidden: The request was valid, but the server is refusing action. The user
                // might not have the necessary permissions for a resource, or may need an account of some sort
                this.statusImage = "stop.svg";
                break;
            case 404:
                // Not Found: The requested resource could not be found but may be available in the future
                this.statusImage = "not_found.svg";
                break;
            case 500:
                // Internal Server Error: Maintenance mode code
                this.statusImage = "error.svg";
                break;
            case 503:
                // Service un-available: Maintenance mode code
                this.statusImage = "forklift.svg";
                break;
            default:
                // No Content: The server successfully processed the request and is not returning any content
                this.statusImage = "success.svg";
                break;
        }
    },
    methods: {
        /*
         * Get an image url by providing the image name.
         */
        getImgUrl(img) {
            return require("../assets/images/" + img);
        }
    }
};
</script>

<style lang="scss">
@import "./../assets/sass/httpStatusPage.scss";
</style>
