<script>
  import { currentPage } from './store.js';

  function loginWithSpotify() {
    // Simulate logging in with Spotify
    setTimeout(() => {
      $currentPage = 'app';
    }, 500);
  }
</script>

<main>
  <h1>Welcome to Fused</h1>
  <p>Discover new music and share your favorites with people around you.</p>
  <form>
    <label for="search">Search for music:</label>
    <input type="text" id="search" name="search">
    <button type="submit">Search</button>
  </form>
  <button on:click={loginWithSpotify}>Log in with Spotify</button>
  <div class="player">
    <p style="font-weight: bold; margin-bottom: 8px;">Currently listening</p>
    <audio controls>
      <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>
  </div>
  <div class="social">
    <p>Share Fused with your friends:</p>
    <a href="https://twitter.com/intent/tweet?url=https%3A%2F%2Fexample.com&text=Check%20out%20this%20awesome%20music%20app!" target="_blank"><i class="fab fa-twitter"></i></a>
    <a href="https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexample.com" target="_blank"><i class="fab fa-facebook"></i></a>
    <a href="https://www.instagram.com/" target="_blank"><i class="fab fa-instagram"></i></a>
  </div>
</main>

<style>
  /* Add your CSS styles here */

  main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
  }

  h1 {
    font-size: 3rem;
    margin-bottom: 32px;
  }

  form {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 16px;
  }

  label {
    margin-right: 8px;
  }

  input[type="text"] {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }

  button[type="submit"] {
    padding: 8px 16px;
    border-radius: 4px;
    border: none;
    background-color: #1db954;
    color: #fff;
    font-weight: bold;
    cursor: pointer;
  }

  .player {
    margin-top: 32px;
  }

  .social {
    margin-top: 32px;
  }

  .social a {
    margin-right: 16px;
    color: #1db954;
    font-size: 2rem;
  }

  .social a:hover {
    color: #000;
  }
</style>
