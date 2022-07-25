<script>
  import { Router, Route, Link } from "svelte-navigator";
  import Home from './lib/Home.svelte';
  import Post from "./lib/Post.svelte";
  import Profile from "./lib/Profile.svelte";
</script>

<Router>
  <header>
    <nav>
      <Link to="/">Home</Link>
      <Link to="profile">Profile</Link>
    </nav>
  </header>

  <main>
    <Route path="/"><Home/></Route>
    <Route path="post/:id"><Post/></Route>
    <Route path="profile"><Profile/></Route>
  </main>
</Router>
