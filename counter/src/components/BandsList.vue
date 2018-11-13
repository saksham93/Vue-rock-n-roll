<template>
    <div>
        <input type="text" placeholder="Add Banc" v-model="newBand" @keyup.enter="addBand()">
        <button @click="addBand()">Add</button>
        <ul>
            <BandItem v-for="band in bands" :key="band.id" :band="band">
            </BandItem>
        </ul>
    </div>
</template>

<script>
import BandItem from './BandItem.vue'

export default {

    name: 'BandsList',
    data () {
        return {
            bands: [
                {
                    id: 1,
                    name: 'Blak',
                    songs: [
                        "Iron Man", "War Pigs"
                    ]
                },
                {
                    id: 2,
                    name: 'ColdPlay',
                    songs: ["Yellow", "Fix Yout"]
                }
            ],
            newBand: null

        }
    },
    components: {
        BandItem
    },
    methods: {
        addBand () {
            this.bands.push({
                name: this.newBand,
                id: this.bands.length+1,
                songs: []
            });
            this.newBand = '';
        }
    }
}
</script>
