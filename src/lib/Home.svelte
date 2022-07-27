<script>
  import { useNavigate, Link } from "svelte-navigator";
  import {onMount} from "svelte";
  import recommendedPosts from '../mocks/recommendedPosts.json';
  import followersPosts from '../mocks/followersPosts.json';

  export let category = 'Home';
  $: posts = category === 'Home' ? recommendedPosts : followersPosts;

  let currentPath;
  onMount(() => {
    currentPath = window.location.pathname;
  });

  const navigate = useNavigate();
  const showPostDetails = id => navigate(`/post/${id}`, )
</script>

<div class="middlebar">
  <header>
    <nav>
      <a href="/" class:active={currentPath === "/"}>
        For you
      </a>
      <a href="/feed/following" class:active={currentPath === "/feed/following"}>
        Following
      </a>
    </nav>
  </header>
  {#each posts as post (post.id)}
    <div class="post" on:click|stopPropagation={()=>showPostDetails(post.id)}>
      <div class="postHeader">
        <img src={post.user.avathar} alt={post.user.username}/>
        <div>{post.user.name}</div>
        <div>. {post.postedOn}</div>
      </div>
      <h2>{post.title}</h2>
      <p>{post.description.substring(0, 200)}...</p>
      <div class='postFooter'>
        <div class='tag'>{post.tag}</div>
        <div>3 min read</div>
        <div><span>. &nbsp;</span> Selected for you</div>
      </div>
    </div>
  {:else}
    <p>Nothing To Show</p>
  {/each}
</div>

<style>
  header {
    margin-bottom: 4vh;
    border-bottom: 0.1px solid #165f7e;
  }
  header nav {
    width: 10vw;
    display: flex;
    justify-content: space-around;
  }

  header a {
    padding-bottom: 1vh;
    width: 50%;
    text-align: center;
    color:  #165f7e;
  }

  .active {
    border-bottom: 4px solid #165f7e;
  }
  .post {
    border-bottom: 0.1px solid #165f7e;
    cursor: pointer;
    margin-bottom: 2vh;
  }
  .postHeader {
    display: flex;
  }
  .postHeader > img {
    border-radius: 50%;
    width: 3%;
  }
  .postHeader > div {
    font-family: sohne, "Helvetica Neue", Helvetica, Arial, sans-serif;
    align-self: center;
    font-size: 75%;
    margin-left: 0.5vw;
    color: rgba(0, 0, 0, 0.6);
    font-weight: 700;
  }

  .postHeader > div + div {
    font-weight: 400;
    color: rgba(0, 0, 0, 0.5);
  }

  .postFooter {
    display: flex;
    font-family: sohne, "Helvetica Neue", Helvetica, Arial, sans-serif;
    color: rgba(0, 0, 0, 0.5);
    margin-bottom: 2%;
  }
  
  .postFooter > div + div {
    font-size: 80%;
    margin-left: 0.5vw;
  }

  .tag {
    border-radius: 8px;
    background-color: rgba(0, 0, 0, 0.1);
    text-align: center;
    font-size: 75%;
    padding: 0.1vh 0.3vw 0.1vh 0.3vw;
  }
</style>
