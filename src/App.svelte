<script>
  import { currentPage } from './store.js';
  import Landing from './Landing.svelte';
  import { writable } from 'svelte/store';

  // Mock data simulating Spotify data
  const mockSongs = [    { id: 1, title: 'Dracula', artist: 'Wallners', rating: 4.5 },    { id: 2, title: 'Sore', artist: 'Sipper', rating: 3.5 },    { id: 3, title: 'Covet', artist: 'Basement', rating: 5 },  ];

  const songs = writable(mockSongs);

  function rateSong(songId, newRating) {
    songs.update((currentSongs) => {
      return currentSongs.map((song) => {
        if (song.id === songId) {
          return { ...song, rating: newRating };
        }
        return song;
      });
    });
  }
</script>

{#if $currentPage === 'landing'}
  <Landing />
{:else if $currentPage === 'app'}
  <main>
    <h1 style="margin-top: 24px; font-size: 2rem; font-weight: bold; text-align: center;">Fused</h1>
    <p style="text-align: center;">Today's jam:</p>
    <div class="player" style="margin: 32px auto;">
      <audio controls>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
      </audio>
    </div>
    <ul style="list-style-type: none; padding: 0; margin: 0;">
      {#each $songs as song (song.id)}
        <li style="display: flex; justify-content: space-between; align-items: center; margin: 8px 0; padding: 16px; border: 1px solid #ccc; border-radius: 4px;">
          <span style="margin-right: 16px; font-weight: bold;">{song.title}</span>
          <span style="margin-right: 12px;">{song.artist}</span>
          <div style="display: flex; align-items: center;">
            <span style="margin-right: 4px;">Rating: {song.rating}</span>
            <button class="rate-up" on:click={() => rateSong(song.id, song.rating + 0.5)}>Rate +0.5</button>
            <button class="rate-down" on:click={() => rateSong(song.id, song.rating - 0.5)}>Rate -0.5</button>
          </div>
        </li>
      {/each}
      {#if $songs.length === 0}
        <p class="empty-list">No songs available</p>
      {/if}
    </ul>
  </main>
{/if}

<style>
  /* Add your CSS styles here */

  button {
    padding: 8px 16px;
    border-radius: 4px;
    border: none;
    background-color: #1db954;
    color: #fff;
    font-weight: bold;
    cursor: pointer;
  }

  .rate-up {
    margin-right: 8px;
  }

  .rate-down {
    margin-right: 8px;
  }

  .empty-list {
    font-weight: bold;
    text-align: center;
    margin-top: 32px;
  }
</style>
