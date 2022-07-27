<script>
    import posts from '../mocks/recommendedPosts.json'

    export let id;
    const post = posts.find(post => post.id === +id);
</script>

<div class="middlebar">
  <h1>{post.title}</h1>
  <p>{post.description}</p>
</div>

<style>
  p {
    text-align: left;
  }
</style>
