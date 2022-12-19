<template>
   <h2>{{ customTitle }} </h2>
   <p> {{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

    <div class="button" >
        <button v-on:click="increse">+1</button>
        <button @click="decrese">-1</button>
    </div>

</template>

<script>
export default {
    props: {
        title: String,
        start: {
            type: Number,
            default: 20,
            // required: true
            validator( value ) {
                return value >= 0
            }
        }
    },
    // name: "Counter"
    data() {
        return {
            counter: this.start
        }
    },
    methods: {  
        getSquareValue() {
            console.log('getSquareValue')
            return this.counter * this.counter
        },
        increse(){
            this.counter++
        },
        decrese(){
            this.counter--
        }
    },
    computed: {
        squareCounter() {
            console.log('computed squareCounter')
            return this.counter * this.counter
        },
        customTitle(){
            return this.title || 'Counter'
        }
    }
}
</script>

<style>

    button{
        background-color: #648887;
        border-radius: 5px;
        border: 1px solid white;
        color: white;
        cursor: pointer;
        margin: 0 5px;
        padding: 5px 15px;
        transition: 0.3s ease-in-out; 
    }

    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out;
    }
    
</style>