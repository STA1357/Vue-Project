<template>
<h1>{{ name }}</h1>
  <div class="form-control">
    <input type="text"
     placeholder="type the post"
     @change= "inputChangeHandler"
           v-model="msg"
    />
    <button class="btn" @click = "addNewPost">Add</button>
    <hr>
    <li v-for="(post,idx) in posts" :key="idx">
      {{ idx }} {{ post }}
      <button @click="deletePost(idx)">delete</button>
    </li>
  </div>
</template>

<script>

export default {
  name: 'Test',
  data () {
    return {
      name: 'lex',
      msg: '',
      posts: []
    }
  },
  methods: {
    inputChangeHandler () {
      console.log(this.msg)
    },
    addNewPost () {
      this.posts.push(this.msg)
    },
    deletePost (idx) {
      this.posts.splice(idx, 1)
    }
  }
}
</script>

<style scoped>

</style>
