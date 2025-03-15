<template>

    <div v-for="(book, index) in books" :key="index">
        <div class="book">
            <div class="readIt" v-if="book.isRead">
                <i class="fa-solid fa-eye"></i>
            </div>
            <div class="book-cover">
                <img :src="book.cover" />

                <!-- <button :class="{isRead : book.isRead}" @click="$emit('toggleReadIt', book.id)">
                <i class="fa-solid fa-eye"></i>
                <span>{{ book.isRead ? "Already Read It" : "Haven't read it yet" }}</span>
                </button> -->

                <button :class="{isRead : book.isRead}" @click="toggleReadIt(book.id)">
                <i class="fa-solid fa-eye"></i>
                <span>{{ book.isRead ? "Already Read It" : "Haven't read it yet" }}</span>
                </button>
            </div>
            <div class="book-details">
                <p class="book-author">{{ book.author }}</p>
                <h3 class="book-title">{{ book.title }}</h3>
                <p><i class="fa-solid fa-hashtag icon"></i> {{ book.isbn }}</p>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    name: "Books",
    emits: ["toggleReadIt"],
    methods: {
        toggleReadIt(id) {
            this.$emit('toggleReadIt', id);
        }
    },
    props: ["books"]
}
</script>

