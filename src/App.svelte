<script>
  import { Router, Route } from "svelte-navigator";
  import Header from "./lib/Header.svelte";
  import Home from './lib/Home.svelte';
  import NewPost from "./lib/NewPost.svelte";
  import Post from "./lib/Post.svelte";
  import Profile from "./lib/Profile.svelte";
  import Search from "./lib/Search.svelte";

  let isWritingNewPost = window.location.pathname === '/newPost';
</script>

<Router>
  <div style="display: flex;">
    {#if !isWritingNewPost}
      <Header/>
    {/if}
    <main>
      <Route path="/"><Home/></Route>
      <Route path="/feed/:category" let:params><Home category={params.category}/></Route>
      <Route path="post/:id" let:params><Post id={params.id}/></Route>
      <Route path="profile"><Profile/></Route>
      <Route path="newPost"><NewPost/></Route>
    </main>
    {#if !isWritingNewPost}
      <Search/>
    {/if}
  </div>
</Router>

<style>
  main {
    width: 55%;
  }
</style>