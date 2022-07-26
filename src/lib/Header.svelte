<script>
  import { Link } from "svelte-navigator";
  import postItIcon from "../assets/postIt.png";
  import home from "../assets/home.png";
  import profile from "../assets/profile.png";
</script>

<header class="sidebar">
  <img class="logo" src={postItIcon} alt=""/>
  <nav>
    <Link to="/">
      <img class="category" src={home} alt=""/>
    </Link>
    <Link to="profile">
      <img class="category" src={profile} alt=""/>
    </Link>
  </nav>
</header>

<style>
  nav {
    display: flex;
    flex-direction: column;
    margin-top: 50%;
  }
  .logo {
    width: 30%;
    height: 7%;
    margin-top: 6vh;
  }
  .category {
    cursor: pointer;
    width: 12%;
    margin-bottom: 3vh;
  }
</style>
