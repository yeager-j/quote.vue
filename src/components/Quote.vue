<template>
    <div class="col-sm-6 col-md-4 col-lg-3">
        <div class="panel panel-default" @click="deleteQuote">
            <div class="panel-body quote">
                <slot></slot>
            </div>
        </div>
    </div>
</template>

<script>
    import { quoteBus } from '../main';

    export default {
        props: ['index'],
        methods: {
            deleteQuote() {
                quoteBus.$emit('deleteQuote', this.index);
            }
        }
    }
</script>

<style scoped>
    .panel-body {
        font-family: 'Arizonia', cursive;
        font-size: 24px;
        color: #6e6e6e;
    }

    .quote {
        cursor: pointer;
    }

    .quote:hover {
        background-color: #ffe2e2;
    }
</style>
