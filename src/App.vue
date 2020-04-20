<template>
  <section id="app">
    <header> 
        <h1> My Music </h1>
    </header>
    <main> 
      <section class="player">
        <h2 class="song-title">Test</h2>
      </section>
    </main>
  </section>
</template>

<script>


export default {
  name: 'App',
  state () {
    return {
      current : {
        title: 'SONG TITLE'
      },
      songs : [
        {
          title: 'Believe',
          artist: 'Roa',
          src: require('./assets/Believe - Roa (Music promoted by Audio Library).mp3')
        },
         {
          title: 'LiQWYD & Le Gang',
          artist: 'Things',
          src: require('./assets/LiQWYD & Le Gang - Things (Free download).mp3')
        },
         {
          title: 'Mango',
          artist: 'Smith The Misters',
          src: require('./assets/Mango by Smith The Misters (Music promoted by Audio Library)_1.mp3')
        },
         {
          title: 'Passionate Affair',
          artist: 'RYYZN',
          src: require('./assets/Passionate Affair (Instrumental) - RYYZN (Music promoted by Audio Library).mp3')
        }
      ]
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: sans-serif;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2em;
  background-color: #212121;
  color: #FFF;
}
</style>
