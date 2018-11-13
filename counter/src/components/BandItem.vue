<template>
    <div>
        <li @click="toggle()">
            {{band.name}}
            <p>
                <span v-show="open">
                    {{band.songs | join}}
                    <input type="text" placeholder="Add song" v-model="songName" @keyup.enter="addSong" @click.stop>
                </span>
            </p>
        </li>
    </div>
</template>

<script>
export default {
    name: 'BandItem',
    data () {
        return {
            open: false,
            songName: ''
        }
    },
    methods: {
        toggle () {
                this.open = !this.open
        },
        addSong () {
            this.band.songs.push(this.songName);
            this.songName = '';
        }
    },
    props: {
        band: Object
    },
   filters: {
    join (arr) {
      return arr.join(', ')
    }
  }
}
</script>

