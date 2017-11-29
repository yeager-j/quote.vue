<template>
    <div class="row">
        <form>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <label for="quote">New Quote</label>
                <textarea id="quote" class="form-control" rows="3" v-model="quote"></textarea>
            </div>

            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <button class="btn btn-primary" @click.prevent="createNew">Add Quote</button>
            </div>
        </form>
    </div>
</template>

<script>
    import { quoteBus } from "../main";

    export default {
        data() {
            return {
                quote: 'New Quote...'
            }
        },
        methods: {
            createNew() {
                if (!this.quote) {
                    return;
                }

                quoteBus.$emit('createQuote', this.quote);
                this.quote = 'New Quote...';
            }
        }
    }
</script>

<style scoped>

</style>
