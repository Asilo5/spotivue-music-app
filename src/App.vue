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
  name: 'App'
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
