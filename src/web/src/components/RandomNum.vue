<template>
    <div>
        <p>Home page</p>
        <p>Random number from backend: {{ randomNumber }}</p>
        <button @click="getRandom">New random number</button>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            randomNumber: 0
        }
    },
    methods: {
        getRandom() {
            // this.randomNumber = this.getRandomInt(1, 100)
            this.randomNumber = this.getRandomFromBackend()
        },
        getRandomFromBackend() {
            const path = `/api/random`
            axios.get(path)
                .then(response => {
                    console.log(response.data.randomNumber)
                    this.randomNumber = response.data.randomNumber
                })
                .catch(error => {
                    console.log(error)
                })
        }
    },
    created() {
        this.getRandom()
    }
}
</script>
