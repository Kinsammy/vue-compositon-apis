<template>
    <div>
        <h1>Options API</h1>
        <input type="text" placeholder="Name" v-model="name"  />
    </div>
    <h1>Composition API</h1>
    <div>
        <h1>ref and watch function</h1>
        <input type="text" placeholder="First Name" v-model="fName"  />
        <input type="text" placeholder="Last Name" v-model="lName"  />
    </div>
    <!-- <div>
        <h1>ref and watch function</h1>
        <input type="text" placeholder="Name" v-model="name"  />
    </div> -->
</template>

<script>
import { ref, watch   } from 'vue'; 
    export default {
        name: "Watch",
        // Options API
        data(){
            return {
                name: ''
            }
        },
        watch: {
            name(newValue, oldValue){
                console.log("Old value", oldValue)
                console.log("New value", newValue)
            }
        },
        // Composition APIs
        setup(){
            // using ref and watch function
            const fName = ref('')
            const lName = ref('Samuel')

            watch([fName, lName], (newValue, oldValue) => {
                console.log("First Name Old value", oldValue[0])
                console.log("First Name New value", newValue[0])
                console.log("Last Name Old value", oldValue[1])
                console.log("Last Name New value", newValue[1])
            }, {
                immediate: true
            })

            return {
                fName,
                lName
            }
        }
        
    
    }
</script>

<style scoped>

</style>