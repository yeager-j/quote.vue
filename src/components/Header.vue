<template>
    <div>
        <h3>Quotes Added</h3>

        <div class="progress">
            <div class="progress-bar progress-bar-striped" role="progressbar" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100" :style="{'width': `${(quotes / maxQuotes) * 100}%`}">{{ quotes }} / {{ maxQuotes }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['quotes', 'maxQuotes']
    }
</script>

<style scoped>

</style>
