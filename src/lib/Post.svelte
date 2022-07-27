<script>
    import posts from '../mocks/recommendedPosts.json'

    export let id;
    const post = posts.find(post => post.id === +id);
</script>

<div class="middlebar">
  <div class='user'>
    <img src={post.user.avathar} alt={post.user.username}/>
    <div>
      <div class="name">{post.user.name}</div>
      <div class="postInfo">{post.postedOn} . 3 min read</div>
    </div>
  </div>
  <h1>{post.title}</h1>
  <p>{post.description}</p>
</div>

<style>
  .user {
    font-family: sohne, "Helvetica Neue", Helvetica, Arial, sans-serif;
    display: flex;
    margin-bottom: 6vh;
  }

  .user > img {
    border-radius: 50%;
    width: 7%;
  }

  .user > div {
    margin-left: 0.7vw;
  }

  .name {
    color: rgba(0, 0, 0, 0.8);
    margin-bottom: 2%;
    align-self: center;
    font-weight: 500;
  }

  .postInfo {
    color: rgba(0, 0, 0, 0.5);
  }
</style>
