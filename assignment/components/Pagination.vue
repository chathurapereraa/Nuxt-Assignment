<template>
  <footer>
    <div class="selector">
      <input
        id="pageCount"
        v-model.number="count"
        type="number"
        name="pageCount"
        min="5"
        max="20"
        step="5"
        value="5"
        @change="setLastPageNum()"
      >
    </div>
    <div class="page__index__wrap">
      <span v-for="(counter,index) in pages " :key="index" class="page__index" @click="setPageNumber(index)">{{ index + 1 }}</span>
    </div>
  </footer>
</template>

<script>
export default {
  data () {
    return {
      red: false,
      count: 5,
      pages: 20,
      pageNum: 1
    }
  },
  methods: {
    setPageNumber (index) {
      this.pageNum = index + 1
      this.$emit('updatePageNumber', this.pageNum)
    },
    setLastPageNum () {
      this.pages = (Math.floor(100 / this.count))
      this.$emit('updatePostCount', this.count)
    }
  }
}
</script>
<style >
footer {
  width: fit-content;
  display: flex;
  gap: 2rem;
  padding: 0.8rem 0rem;
}
input[type="number"] {
  width: 30px;
  height: 26px;
}
.page__index,
.more__sign,
.last__page__index {
  width: 26px;
  height: 26px;
}
.page__index,
.more__sign,
.last__page__index {
  display: grid;
  place-items: center;
  margin: 0 0.5rem;
  border: 1px solid rgba(212, 199, 199, 0.904);
}
.page__index__wrap {
  display: flex;
  align-items: center;
}
.page__index__wrap span{
  cursor: pointer;

}
.page__index__wrap span:hover{
  background: rgb(221, 216, 216);
}
.page__index__wrap span:enabled{
  background: rgb(221, 216, 216);
  border: 5px solid rgb(144, 24, 168);
}
.page__index.red {
  background: rgba(184, 183, 183, 0.856);
  border: 1.5px solid rgb(204, 34, 34);
}
</style>
