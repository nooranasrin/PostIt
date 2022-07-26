<script>
    import {useParams} from 'svelte-navigator';
    import posts from '../mocks/posts.json'

    const params = useParams();
    const post = posts.find(post => post.id === +$params.id);
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
