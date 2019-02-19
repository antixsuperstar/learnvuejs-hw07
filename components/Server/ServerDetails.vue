<template>
    <div class="col-xs-12 col-sm-6">
        <p>{{ server.id }}: {{ server.status }}</p>
        <button
            @click="setNormal(server)">
            set to normal
        </button>
    </div>

</template>

<script>
    import { eventBus } from "../../main";

    export default {
        data: () => { return {
            server: {}
        }},
        methods: {
            setNormal(server) {
                eventBus.$emit('setNormal', server);
            }
        },
        created() {
            eventBus.$on('showServerDetails', (server) => {
                this.server = server
            });
        }
    }
</script>

<style>

</style>
