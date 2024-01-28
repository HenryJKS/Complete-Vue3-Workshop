<script>
export default {
    data: () => ({
        count: 10,
        counterTitle: "Counter Standard",
        incrementAmount: 8
    }),
    computed: {
        displayTile() {
            if (this.count > 20) {
                return "Counter Standard - Very Long" 
            } else {
                return "Counter Standard"
            }
        },
        optimizedIncrementAmount() {
            return this.displayTile.length * this.incrementAmount
        }
    },
    methods: {
        incrementCount(newAmount, event) {
            console.log(newAmount)
            console.log(event)
            this.count += this.optimizedIncrementAmount
        }
    }
}
</script>

<template>
    <h2>{{ displayTile }}</h2>
    <p :data-increment-by="incrementAmount">{{ incrementAmount }}</p>
    <button @click="incrementCount">Increment Count</button>
    <h1>{{ incrementAmount }}</h1>
    <p>{{  optimizedIncrementAmount }}</p>
    <div>
        <label for="incrementAmount">Increment By:</label>
        <input type="text" v-model="incrementAmount">
    </div>
</template>