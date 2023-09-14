<template>
    <div>
        <h1>Replacing Methods in vue</h1>
        <hr />
        <h2>The methods using data</h2>
        <h2>{{ name }}</h2>
        <button @click="setName">Change Name</button>
        <hr />
        <h2>The methods using ref and JavaScript function</h2>
        <h2>{{ count }}</h2>
        <button @click="incrementCount">Increment Count</button>
        <hr />
        <h2>The methods using reactive, toRefs  and JavaScript function</h2>
        <h2>{{ fName }} {{ lName }}</h2>
        <button @click="changeHero">Change Hero</button>
    </div>
</template>

<script>
import { ref, reactive, toRefs } from 'vue'; 
    export default {
        name: "Methods",
        data() {
            return {
                name: "Samuel"
            }
        },
        methods: {
            setName() {
                this.name = "Hannah"
            },
        },
        // the other way to replace methods in vue
        setup() {
            // Using ref function and js function
            const count = ref(0)
            function incrementCount() {
                count.value++
            }

            // using reactive and toRefs function
            const state = reactive({
                fName: "John",
                lName: "Doe"
            })
            function changeHero() {
                state.fName = "Samuel"
                state.lName = "Fanu"
            }
            return {
                count,
                incrementCount,
                
                ...toRefs(state),
                changeHero,
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>