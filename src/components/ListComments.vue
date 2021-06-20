<template>
  <div >
    <FormComment v-on:add-comment="addComment" class="container mt-4"></FormComment>
    <div class="comments form-todo form-group">
      <div class="comments__nostyle" v-if="comments.length <= 0">
        <p >No comments yet...</p>
      </div>
      <div
        v-else
        class="list-group-item"
        v-for="(comment, index) in allComments"
        v-bind:key="index"
      >
        <span class="comment__author"
          >Author: <strong>{{ comment.author }}</strong></span
        >
        <p>{{ comment.content }}</p>
        <div>
          <a href="#" title="Remove" v-on:click.prevent="removeComment(index)"
            >Remove</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FormComment from "./FormComments.vue";
export default {
  name: "ListComments",

  components: {
    FormComment
  },

  data() {
    return {
      comments: []
    };
  },

  mounted() {},

  methods: {
    addComment(comment) {
      this.comments.push(comment);
      console.log(this.comments);
    },

    removeComment(index) {
      this.comments.splice(index, 1);
    }
  },

  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        author: comment.author.trim() === "" ? "Anonymous" : comment.author
      }));
    }
  }
};
</script>

<style>

.comments__nostyle {
  text-align: center;
  padding-top: 1rem;
}

.comments{
  padding-top: 1rem;
}

.form__coments {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
</style>
