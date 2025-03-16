<template>

<h1>📖 Add a new Book</h1>
    
    <div class="header-btns">
      <button class="btn" @click="$emit('closeAddBook')">
        Close x
      </button>
    </div>
 
    <form class="add-form">
        <div class="form-control">
        <label>Title</label>
        <input
            v-model="title"
            type="text"
            name="text"
            placeholder="Add Book Title"
        />
        </div>
        <div class="form-control">
        <label>Book Cover</label>
        <input 
            type="text" 
            name="cover" 
            placeholder="Add Cover" 
            v-model="cover"
        />
        </div>
        <div class="form-control">
        <label>Author</label>
        <input
            type="text"
            name="author"
            placeholder="Add Author"
            v-model="author"
        />
        </div>
        <div class="form-control">
        <label>ISBN#</label>
        <input 
            type="text" 
            name="isbn" 
            placeholder="Add ISBN"
            v-model="isbn" 
        />
        </div>
        <div class="form-control form-control-check">
        <input 
            type="checkbox" 
            name="readIt" 
            id="readIt"
            v-model="isRead" 
        />
        <label for="readIt">I have read it already</label>
        </div>
 
        <button @click.prevent="addBook" type="submit" class="btn btn-block">Save Book</button>
    </form>

</template>

<script>
export default {
    name: 'AddBook',
    emits: ['closeAddBook', 'addBook'],
    props: ['nextId'],
    data(){
        return {
            id: null,
          title: "",
          cover: "",
          isRead: false,
          isbn: "",
          author: ""
        }
    },
    methods: {
        addBook() {
            if(!this.title || !this.cover) {
                alert('Please enter the title and cover.')
            } else {
                const newBook = {
                    id: this.nextId,
                    title: this.title,
                    cover: this.cover,
                    isRead: this.isRead,
                    isbn: this.isbn,
                    author: this.author
                }
                this.$emit('addBook', newBook);

                this.title = "";
                this.cover = "";
                this.isRead = "";
                this.isbn = "";
                this.author = "";

                this.$emit('closeAddBook', newBook);
            }
        }
    }
}
</script>