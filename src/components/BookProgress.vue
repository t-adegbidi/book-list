
<template>

    <div class="books-read">
        <label for="progress">Your Progress</label><br />
        <progress :value="booksReadPercent" max="100"></progress>
        <p>{{ booksReadMessage }}</p>
    </div>

</template>

<script>

    export default {
        name: 'Book Progress',
        props: ['books'],
        computed: {
            booksRead() {
                return this.books.filter(book => book.isRead).length;
            },
            booksReadPercent() {
                return Math.round(this.booksRead / this.books.length * 100);
            },
            booksReadMessage() {
                return this.booksReadPercent >= 100 ? 'All the books were read. Congrats!' : `${ this.booksRead } out of ${ this.books.length } books read`;
            }
        }
    }

</script>