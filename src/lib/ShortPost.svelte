<script>
  import {
      useNavigate
  } from "svelte-navigator";

  export let post = {};
  const navigate = useNavigate();

  const showPostDetails = id => navigate(`/post/${id}`, )
</script>

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

<style>
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
