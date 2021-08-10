<template>
  <div class="tag-container">
    <Tag
        :tagColor="color"
        v-for="(tag,index) in tags"
        :tag="tag"
        :index="index"
        @removeClickedEvent="removeClicked($event)"
    />
    <input
        type="text"
        @keydown.enter="addTag"
        @keydown.backspace="removeTag"
    >
    <span v-if="error">Bu değer zaten ekli</span>
  </div>
</template>

<script>
import Tag from "./Tag"

export default {
  data() {
    return {
      tags: ["deneme", "test"],
      error: false
    }
  },
  components: {
    Tag
  },
  methods: {
    addTag(event) {
      let text = event.target;

      if (text.value.length > 0) {
        let isControl = this.tags.filter(tag => tag.toLocaleLowerCase() === text.value.toLowerCase())

        if (!isControl.length == 0) {
          this.error = true;
        } else {
          this.tags.push(text.value);
          text.value = '';
        }
      }
    },
    removeTag(event) {
      if (event.target.value <= 0) {
        this.tags.pop();
      }
    },
    removeClicked(index) {
      this.tags.splice(index, 1)
    }
  },
  props: {
    value: {
      required: false
    },
    color: {
      type: String,
      required: false,
      default: 'primary'
    }
  },
  created() {
    if (this.value) {
      this.tags = this.value.split(',');
    }
  },
  watch: {
    tags() {
      this.$emit("input", this.tags.join(','))
    }
  }
}
</script>

<style scoped lang="scss">
.tag-container {
  border: 1px solid #000000;
  padding: 10px;
}
</style>