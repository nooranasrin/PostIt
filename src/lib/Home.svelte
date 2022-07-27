<script>
  import {onMount} from "svelte";
  import recommendedPosts from '../mocks/recommendedPosts.json';
  import followersPosts from '../mocks/followersPosts.json';
  import ShortPost from "./ShortPost.svelte";

  export let category = 'Home';
  $: posts = category === 'Home' ? recommendedPosts : followersPosts;

  let currentPath;
  $: onMount(() => currentPath = window.location.pathname);

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
    <ShortPost post={post}/>
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
</style>
