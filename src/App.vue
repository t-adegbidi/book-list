<template>
  
  <div class="container" v-if="!showAddBook">
    <h1>📖 My Book List</h1>
    <div class="header-btns">
      <button class="btn" @click="showAddBook = true">
        Add Book +
      </button>
      <button class="btn" @click="tableView = !tableView">
        {{tableView ? 'List View' : 'Table View'}}
      </button>
    </div>
 
    <div class="books-container">

      <Books @toggleReadIt="toggleReadIt" :tableView="tableView" :books="books" @addBook="addBook" />

      <BookProgress :books="books" />

    </div>
  </div>

  <div class="container" v-else>
    <AddBook :nextId="nextId" @addBook="submitBook" @closeAddBook="showAddBook = false" />
  </div>

</template>

<script>

import Books from "./components/Books.vue";
import AddBook from "./components/AddBook.vue";
import BookProgress from "./components/BookProgress.vue";

export default {
  name: "App",
  components: {
    Books,
    AddBook,
    BookProgress
  },
  data() {
    return {
      showAddBook: false,
      tableView: false,
      books: [
        {
          id: 1,
          title: "A Short History of Europe",
          cover:
            "https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1535542619i/40772628.jpg",
          isRead: true,
          isbn: "0-395-07157-8",
          author: "Simon Jenkins",
          synopsis: "In this dazzling new history, bestselling author Simon Jenkins grippingly tells the story of its evolution from warring peoples to peace, wealth and freedom - a story that twists and turns from Greece and Rome, through the Dark Ages, the Reformation and the French Revolution, to the Second World War and up to the present day."
        },
        {
          id: 2,
          title: "Penguin Classics",
          cover:
            "https://m.media-amazon.com/images/I/91cKrZxBuwL._AC_UF1000,1000_QL80_.jpg",
          isRead: false,
          isbn: "0-395-07157-8",
          author: "Henry Eliot",
          synopsis: "The Penguin Classics Book covers all the greatest works of fiction, poetry, drama, history, and philosophy in between, this reader's companion encompasses 500 authors, 1,200 books, and 4,000 years of world literature, from ancient Mesopotamia to World War I."
        },
        {
          id: 3,
          title: "Becoming",
          cover:
            "https://m.media-amazon.com/images/I/81-6EJJzxvL.jpg",
          isRead: false,
          isbn: "0-395-07157-8",
          author: "Michelle Obama",
          synopsis: "“Becoming” is an autobiography detailing the highs and lows of Michelle Obama's incredible journey from humble beginnings in the less glamourous South Side of Chicago, to the grandeur of the White House and life as America's first African-American First Lady."
        },
        {
          id: 4,
          title: "Sonnets",
          cover:
            "https://m.media-amazon.com/images/I/715hva4FrAL._AC_UF1000,1000_QL80_.jpg",
          isRead: false,
          isbn: "0-395-07157-8",
          author: "James Anthony",
          synopsis: "Shakespeare wrote 154 sonnets published in his 'quarto' in 1609, covering themes such as the passage of time, mortality, love, beauty, infidelity, and jealousy. The first 126 of Shakespeare's sonnets are addressed to a young man, and the last 28 addressed to a woman – a mysterious 'dark lady'."
        }
      ]
    }
  },
  methods: {
    submitBook(newBook) {
      this.books.push(newBook);
    },
    toggleReadIt(id){
      this.books.forEach(book => {
        if(book.id === id) {
          book.isRead = !book.isRead;
        }
      });
    }
  },
  computed: {
    nextId() {
      return Math.max(...this.books.map(el => el.id)) + 1;
    }
  }
}
</script>

<style scoped>
  
 
</style>
