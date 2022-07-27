<script>
  import postItIcon from "../assets/postIt.png";
  import home from "../assets/home.png";
  import profile from "../assets/profile.png";
  import newPost from "../assets/newPost.png";
</script>

<header class="sidebar">
  <img class="logo" src={postItIcon} alt=""/>
  <nav>
    <a href="/">
      <img class="category" src={home} alt=""/>
    </a>
    <a href="profile">
      <img class="category" src={profile} alt=""/>
    </a>
    <a href="/newPost">
      <img class="category" src={newPost} alt=""/>
    </a>
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
