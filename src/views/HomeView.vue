<template>
  <div class="home">
    <h1>Hello View :)</h1>
    <div v-if="showBook">
    <ul>
      <li @click="toggleIsFav(book)" v-for="book in books" :key="book.title" :class="{ fav: book.isFav}">
        <img :src="book.img" :alt="book.title" />
        <h3>{{ book.title }}</h3>
      </li>
    </ul>
      
    </div>
    <button @click="toggleShowBox">
      <span v-if="showBook">Hide Books</span>
      <span v-else>Show Books</span>
    </button>
    <br/>

    <!-- mouse events -->
    <!-- <div class="box" @mouseover="handleEvent($event, 5)">mouseover</div>
    <div class="box" @mouseleave="handleEvent">mouseleave</div>
    <div class="box" @dblclick="handleEvent">dblclick</div>
    <div class="box" @mousemove="handleMousemove">position - {{ x }} {{ y }}</div> -->
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      showBook: true,
      books: [
        {title: "The Name og the Wind", author: "Brandon Sanderson", img: require('@/assets/1.jpg'), isFav: true},
        {title: "The Final Dynasti", author: "Neo Anderson", img: require('@/assets/2.jpg'), isFav: false},
        {title: "The Final Empire", author: "Peter Anderson", img: require('@/assets/3.jpg'), isFav: true}
      ],
      x: 0,
      y: 0,
    }
  },
  methods: {
    toggleShowBox() {
      this.showBook = !this.showBook
    },
    toggleIsFav(book: any) {
      book.isFav = !book.isFav
    }
  },
  // computed: {
  //   filteretBooks() {
  //     return this.books.filter((book: any) => book.isFav)
  //   } 
  // }
});
</script>

<style lang="scss">
  body {
    background-color: #eee;
    max-width: 960px;
    margin: 20px auto;
  }
</style>

<style scoped lang="scss">

  p, h3, ul {
    margin: 0;
    padding: 0;
  }

  li {
    list-style-type: none;
    background-color: #fff;
    margin: 20px auto;
    padding: 10px 20px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    &.fav {
      background-color: #ff9ed2;
      color: white;
    }
  }

  .box {
    padding: 100px;
    width: 400px;
    text-align: center;
    background-color: #ddd;
    margin: 20px;
    display: inline-block;
  }
</style>