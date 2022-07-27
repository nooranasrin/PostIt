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
      <div class="header">
        <img src={post.user.avathar} alt={post.user.username}/>
        <div>{post.user.name}</div>
        <div>. {post.postedOn}</div>
      </div>
      <h2>{post.title}</h2>
      <p>{post.description.substring(0, 200)}...</p>
      <div class='header'>
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
  }

  .active {
    border-bottom: 4px solid #165f7e;
  }
  .post {
    border-bottom: 0.1px solid #165f7e;
    cursor: pointer;
    margin-bottom: 2vh;
  }
  .header {
    display: flex;
    font-family: sohne, "Helvetica Neue", Helvetica, Arial, sans-serif;
    margin-bottom: 2%;
    color: rgba(0, 0, 0, 0.5);
    align-self: center;
  }
  .header > img {
    border-radius: 50%;
    width: 3%;
  }
  .header > div {
    font-size: 80%;
    margin-left: 0.5vw;
    font-weight: 700;
  }

  .header > div + div {
    font-weight: 400;
  }

  .tag {
    border-radius: 8px;
    background-color: rgba(0, 0, 0, 0.1);
    text-align: center;
    font-size: 75%;
    padding: 0.1vh 0.3vw 0.1vh 0.3vw;
    margin-left: 0 !important;
  }
</style>
