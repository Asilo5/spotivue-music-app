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
        <section class="songs-list">
          <button v-for="song in songs" 
                  :key="song.src" 
                  @click="play(song)"
                  :class="(song.src == current.src) ? 'song playing' : 'song' ">
            {{ song.title }} - {{ song.artist }}
          </button>
        </section>
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
          title: 'Things',
          artist: 'LiQWYD & Le Gang',
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
  background-color: goldenrod;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  font-size: 4em;
}

main {
  margin: 20px;
  background-color: darkkhaki;
  border-radius: 50%;
  width: 50%;
  height: 37em;
  margin: auto;
}

.song-title {
  text-align: center;
  font-size: 2em;
  text-transform: uppercase;
  margin-top: 20px;
  padding-top: 80px;
}

.song-title span {
  font-weight: 400;
  font-style: italic;
}

.controls {
  display: flex;
  justify-content: center;
  padding: 30px;
}

button {
  padding: 10px;
  margin: 5px;
  border-radius: 10px;
  border: none;
  color: white;
}

button:hover {
  opacity: 0.9;
  cursor: pointer;
} 

.play, .pause {
  font-size: 20px;
  font-weight: 700;
  padding: 15px 25px;
  margin: 0 15px;
  background-color: darkolivegreen;
}

.prev, .next {
  background-color: darkolivegreen;
}

.playlist {
  text-align: center;
  padding: 10px;
}

.songs-list {
  display: flex;
  justify-content: center;
  flex-direction: column;
  height: 13em;
  overflow: scroll;
}

h3 {
  padding: 5px;
}

.songs-list button {
  width: 50%;
  margin: 5px auto;
  background-color: transparent;
  font-size: 15px;
}

.songs-list button:hover {
  background-color: darkolivegreen;
}

.songs-list .song.playing {
  background-color: darkolivegreen;
}


</style>
