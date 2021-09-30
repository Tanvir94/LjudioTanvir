<template>
  <div id="app">
     <header>
     <h1>My Music</h1>
     </header>

     <main>
      <section class="player">
        <h2 class="song-title">{{ current.title }} - <span>{{ current.artist}}
          </span></h2>
          <div class="control">
            <button class="prev">Prev</button>
            <button class="play" v-if="!isPlaying">Play</button>
            <button class="pause" v-else>Pause</button>
            <button class="next">Next</button>
          </div>
        {{ songs[0].src }}
        </section>

     </main>

  
  </div>
</template>

<script>


export default {
  name: 'App',
  data () {
    return {
      current: {},
      index: 0,
      isPlaying: false,
    songs: [
      {
        title: 'Grateful',
        artist: 'Neffex',
        src: require('./assets/neffex-grateful.mp3')
    
  },
        {

          title:  'Invincible',
          artist: 'Deaf Kev',
          src:  require('./assets/src_assets_deaf-kev-invincible.mp3')
          }
          ],
          player: new Audio()
          }

  },
  methods: {
    play (song) {
      if (typeof song.src !="undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }
      this.player.play();
      this.isPlaying = true;
      }
    },
  created () {
  this.current = this.songs[this.index]
  this.player.src = this.current.src;
  //this.player.play();


  }
  }

</script>

<style>

</style>
}