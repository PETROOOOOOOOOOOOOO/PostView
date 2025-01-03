<template>
  <div v-show="posts.length > 0">
    <h3>Список постів</h3>
    <transition-group name="postList">
      <post-item
          v-for="post in posts"
          :key="post.id"
          :post="post"
          @remove="$emit('remove', post)"/>
    </transition-group>
  </div>
  <h2 v-show="posts.length === 0 " style="color:red">
    Список постів пустий
  </h2>
</template>

<script>
import PostItem from "@/components/PostItem.vue";

export default {
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.postList-item{
  display: inline-block;
  margin-right: 10px;
}
.postList-enter-active,
.postList-leave-active {
  transition: all 1s ease;
}
.postList-enter-from,
.postList-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
</style>