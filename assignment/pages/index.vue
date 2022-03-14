<template>
  <div class="posts__display">
    <Header :num-of-pages="filteredPostsCount" :page-number="pageNumber" />
    <p>test</p>
    <table>
      <tr>
        <th>#</th>
        <th>Title</th>
        <th>Body</th>
        <th>{{ filteredPostsCount }}</th>
      </tr>
      <Posts v-for="post in filteredPosts" :key="post.id" :post="post" />
    </table>
    <Pagination @updatePostCount="filterPosts" @updatePageNumber="updatedPageNumber" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      posts: [],
      filteredPosts: [],
      filteredPostsCount: 5,
      pageNumber: 1
    }
  },
  async fetch () {
    this.posts = await fetch('https://jsonplaceholder.typicode.com/posts').then(
      res => res.json()
    )
    this.updatePostsTable()
  },
  methods: {
    filterPosts (count) {
      this.filteredPostsCount = count
      this.updatePostsTable()
    },
    updatedPageNumber (pageNumber) {
      this.pageNumber = pageNumber
      this.updatePostsTable()
    },
    updatePostsTable () {
      this.filteredPosts = (this.posts).slice((this.pageNumber - 1) * this.filteredPostsCount, this.pageNumber * this.filteredPostsCount)
    }
  }
}
</script>
<style scoped>
  .posts__display{
    width: 80%;
    margin: 0 auto;
  }
</style>
