<script>
  import { useNavigate } from "svelte-navigator";
  import posts from '../mocks/posts.json';

  const navigate = useNavigate();
  let newPost = {title: "", description: ""}; 
  let newPosts = posts.slice(0);

  const showPostDetails = id => navigate(`/post/${id}`, )
  const savePost = () => 
    newPosts = [ {...newPost, id: newPosts.length + 1}, ...newPosts];
</script>

<div>
  <textarea bind:value={newPost.title} placeholder='Title'/>
  <br/>
  <textarea bind:value={newPost.description}  placeholder="Enter your post here...."/>
  <button on:click={savePost}>Post</button>
</div>

<h1>Posts</h1>
{#each newPosts as post (post.id)}
  <div on:click={()=>showPostDetails(post.id)}>
    <h2>{post.title}</h2>
    <p>{post.description.substring(0, 200)}...</p>
  </div>
{:else}
  <p>Nothing To Show</p>
{/each}

<style>
  textarea {
		padding: 0.5em;
		border-radius: 4px;
	}
  button {
    margin-left: 80%;
    width: 8rem;
  }
  div {
    border: 1px solid white;
    margin: 2rem;
    border-radius: 8px;
    text-align: left;
    padding: 1rem;
    cursor: pointer;
  }
</style>
