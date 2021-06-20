<template>
  <div>
    <div>
      <h1>Comments</h1>
      <hr />
      <div class="form-todo form-group">
        <p>
          <input
            type="text"
            placeholder="Your name"
            name="author"
            class="form-control"
            v-model="author"
          />
        </p>
        <p>
          <textarea
            placeholder="Your comment"
            class="form-control"
            v-model="content"
          ></textarea>
        </p>
        <button v-on:click="FormAddComment" class="btn btn-primary">
          Submit
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      author: "",
      content: ""
    };
  },
  methods: {
    FormAddComment() {
      if (this.content.trim() === "") {
        return;
      }

      this.$emit("add-comment", {
        author: this.author,
        content: this.content
      });

      this.author = "";
      this.content = "";
    }
  }
};
</script>
