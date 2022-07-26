<script>
  import { useNavigate } from "svelte-navigator";
  import posts from '../mocks/posts.json';

  const navigate = useNavigate();
  const showPostDetails = id => navigate(`/post/${id}`, )
</script>

<div class="middlebar">
  {#each posts as post (post.id)}
    <div class="post" on:click={()=>showPostDetails(post.id)}>
      <div class="postHeader">
        <img src={post.user.avathar} alt={post.user.username}/>
        <div>{post.user.name}</div>
        <div>. {post.postedOn}</div>
      </div>
      <h2>{post.title}</h2>
      <p>{post.description.substring(0, 200)}...</p>
    </div>
  {:else}
    <p>Nothing To Show</p>
  {/each}
</div>

<style>
  .post {
    border-bottom: 0.1px solid #165f7e;
    margin: 2rem;
    cursor: pointer;
  }
  .postHeader {
    display: flex;
  }
  .postHeader > img {
    border-radius: 50%;
    width: 3%;
  }
  .postHeader > div {
    align-self: center;
    font-size: 75%;
    margin-left: 0.5vw;
    color: rgba(0, 0, 0, 0.7);
    font-weight: 700;
  }

  .postHeader > div + div {
    font-weight: 400;
    color: rgba(0, 0, 0, 0.5);
  }
</style>
