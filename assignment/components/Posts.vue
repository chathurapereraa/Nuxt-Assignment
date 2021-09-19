<template>
  <tr>
    <td>{{ post.id }}</td>
    <td>{{ post.title }}</td>
    <td>
      {{ post.body }}
    </td>
  </tr>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style lang="sass">
</style>
