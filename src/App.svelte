<script>
  import { Router, Route } from "svelte-navigator";
  import Header from "./lib/Header.svelte";
  import Home from './lib/Home.svelte';
  import Post from "./lib/Post.svelte";
  import Profile from "./lib/Profile.svelte";
  import Search from "./lib/Search.svelte";
</script>

<Router>
  <div style="display: flex;">
   <Header/>
    <main>
      <Route path="/"><Home/></Route>
      <Route path="/feed/:category" let:params><Home category={params.category}/></Route>
      <Route path="post/:id" let:params><Post id={params.id}/></Route>
      <Route path="profile"><Profile/></Route>
    </main>
    <Search/>
  </div>
</Router>

<style>
  main {
    width: 55%;
  }
</style>