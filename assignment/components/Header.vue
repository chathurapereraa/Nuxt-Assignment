<template>
  <div class="header__container">
    <div class="posts__counter">
      <h2><span>100</span> Total Posts</h2>
    </div>

    <div class="page__counter">
      <h2>Page <span>{{ pageNumber }}</span>/<span>{{ calPageCount() }}</span></h2>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pageNumber: {
      type: Number,
      default: 1
    },
    numOfPages: {
      type: Number,
      default: 20
    }
  },
  methods: {
    calPageCount () {
      return Math.floor(100 / this.numOfPages)
    }
  }
}
</script>

<style >
.header__container{
    width: 40%;
    height:50px;
    display:flex;
    align-items: center;
    margin: 3rem 0;

}

</style>
