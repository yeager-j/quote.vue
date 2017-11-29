<template>
    <div class="container">
        <app-header :quotes="quotes.length" :maxQuotes="maxQuotes"></app-header>

        <app-new-quote></app-new-quote>

        <app-quote-grid :quotes="quotes"></app-quote-grid>

        <div class="alert alert-info">
            <b>Hey, listen!</b> You can delete a quote by clicking on it.
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';
    import { quoteBus } from "./main";

    export default {
        created() {
            quoteBus.$on('createQuote', event => {
                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push(event);
                } else {
                    alert('Too many quotes! You have a max of ' + this.maxQuotes);
                }
            });

            quoteBus.$on('deleteQuote', event => {
                this.quotes.splice(event, 1);
            });
        },
        data() {
            return {
                maxQuotes: 10,
                quotes: [
                    'Hello World!',
                    'Another Quote'
                ]
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
