<template>
    <div class="container">
        <appHeader :quoteCount='quotes.length' :maxQuotes='maxQuotes'></appHeader>
        <app-new-quote @quoteAdded='newQuote'></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted='deleteQuote'></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a quote to delete it !
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue'
    import NewQuote from './components/NewQuote.vue'
    import Header from './components/Header.vue'

    export default {
        data: function(){
            return {
                quotes: [
                    'Just a sample quote'
                ],
                maxQuotes: 10
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        },
        methods: {
            newQuote(quote){
                if(this.quotes.length >= this.maxQuotes){
                    alert('Please delete quotes first !!')
                }
                else{
                    this.quotes.push(quote)
                }
            },
            deleteQuote(index){
                this.quotes.splice(index, 1)
            }
        }
    }
</script>

<style>
</style>
