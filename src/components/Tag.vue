<template>
  <span class="tag" :class="theme">
    <span class="content">{{ tag }}</span>
    <span class="close" @click="$emit('removeClickedEvent',index)">X</span>
  </span>
</template>

<script>
export default {
  props: ["tag", "index", "tagColor"],
  data() {
    return {
      theme: null
    }
  },
  created() {
    this.theme = this.tagColor
  }
}
</script>

<style scoped lang="scss">
.tag {
  padding: 10px;
  margin-right: 10px;
  border-radius: 10px;

  &.primary {
    background-color: rgba(red, 0.2);
  }

  &.secondary {
    background-color: rgba(green, 0.2);
  }

  .close {
    cursor: pointer;
  }
}
</style>