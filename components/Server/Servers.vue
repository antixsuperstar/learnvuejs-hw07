<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <li
                    class="list-group-item"
                    v-for="server in servers">
                <a
                        href="#"
                        @click="showServerDetails(server)"
                        >
                    Server #{{ server['id'] }}
                </a>
            </li>
        </ul>
    </div>
</template>

<script>
    import { eventBus } from "../../main";

    export default {
        data:() => { return {
            servers: [
                { id: 1, status: 'Overload' },
                { id: 2, status: 'Critical' },
                { id: 3, status: 'Offline' },
                { id: 4, status: 'Idle' },
                { id: 5, status: 'Normal' },
            ]};
        },
        methods: {
            showServerDetails: (server) => {
                eventBus.$emit('showServerDetails', server)
            }
        },
        created() {
            eventBus.$on('setNormal', (server) => {
                server['status'] = 'Normal';
            });
        }
    }
</script>

<style>

</style>
