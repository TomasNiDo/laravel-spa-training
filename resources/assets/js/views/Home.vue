<template>
    <div class="container">
    <article class="message is-primary" v-for="status in statuses">
        <div class="message-header">
            <p>
                {{ status.user.name }}
            </p>
            <p>
                {{ postedOn(status) }}
            </p>
        </div>

        <div class="message-body" v-text="status.body"></div>
    </article>
    </div>
</template>

<script>
    import moment from 'moment';
    import Status from '../models/Status';

    export default {
        data() {
            return {
                statuses: [],
            }
        },

        methods: {
            postedOn(status) {
                return moment(status.created_at).fromNow();
            }
        },

        created() {
            Status.all(statuses => this.statuses = statuses);
        }
    }
</script>
