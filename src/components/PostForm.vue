<template>
  <div>
    <form @submit.prevent>
      <h3> Створити пост</h3>
      <my-input
          v-model="post.title"
          type="text"
          placeholder="Назва"/>
      <my-input
          v-model="post.body"
          type="text"
          placeholder="Опис"/>
      <my-button
          style="align-self: flex-end; margin-top:15px"
          @click="createPost"
      >Створити
      </my-button>
    </form>
  </div>
</template>

<script>
import MyInput from "@/components/UI/MyInput.vue";

export default {
  components: {MyInput},
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: '',
      }
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>