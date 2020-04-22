<template>
  <section id="app">
    <header> 
        <h1> My Music </h1>
    </header>
    <main> 
      <section class="player">
        <h2 class="song-title"> {{ current.title }} - <span> {{ current.artist }} </span></h2>
      </section>
      <section class="controls">
        <button class="prev" @click="prev">Prev</button>
        <button class="play" v-if="!isPlaying" @click="play">Play</button>
        <button class="pause" v-else @click="pause"> Pause </button>
        <button class="next" @click="next ">Next</button>
      </section>
      <section class="playlist">
        <h3>The Playlist</h3>
        <button v-for="song in songs" 
                :key="song.src" 
                @click="play(song)"
                :class="(song.src == current.src) ? 'song playing' : 'song' ">
          {{ song.title }} - {{ song.artist }}
        </button>
      </section>
    </main>
  </section>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      current : {},
      index : 0,
      isPlaying: false,
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
      ],
      player: new Audio()
    }
  },
  methods: {
    play (song) {
      if(typeof song.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }

      this.player.play();
      this.isPlaying = true;
    },

    pause () {
      this.player.pause();
      this.isPlaying = false;
    },
    next () {
      this.index++;
      if(this.index > this.songs.length - 1) {
        this.index = 0;
      }

      this.current = this.songs[this.index];
      this.play(this.current);
    },
    prev () {
      this.index--;
      if(this.index < 0) {
        this.index = this.songs.length - 1;
      }

      this.current = this.songs[this.index];
      this.play(this.current);
    }
  },
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
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
