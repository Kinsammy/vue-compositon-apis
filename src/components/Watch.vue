<template>
    <div>
        <h2>Options API</h2>
        <input type="text" placeholder="Name" v-model="name"  />
    </div>
    <h1>Composition API</h1>
    <div>
        <h2>ref and watch function</h2>
        <input type="text" placeholder="First Name" v-model="fName"  />
        <input type="text" placeholder="Last Name" v-model="lName"  />
    </div>
    <div>
        <h2>reactive function and watch function</h2>
        <input type="text" placeholder="First Name" v-model="firstName"  />
        <input type="text" placeholder="Last Name" v-model="lastName"  />
    </div>
    <div>
        <h1>Deep Watcher</h1>
        <input type="text" placeholder="Hero Name" v-model="options.heroName"  />
    </div>
</template>

<script>
import { ref, watch, reactive, toRefs} from 'vue'; 
import _ from 'lodash'
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

            // Using reactive function and toRefs 
            const state = reactive({
                firstName: '',
                lastName: ''
            })

            watch( () => {
            return { ...state }
            },
            function(newValue, oldValue){
                console.log("First Name Old value", oldValue.firstName)
                console.log("First Name New value", newValue.firstName)
                console.log("Last Name Old value", oldValue.lastName)
                console.log("Last Name New value", newValue.lastName)
            })

            // Deep watcher using lodash
            const profile = reactive({
                options: {
                    heroName: ''
                }
            })

            watch( 
                () => _.cloneDeep(profile.options),
                function(newValue, oldValue){
                    console.log("Hero Name Old value", oldValue.heroName)
                    console.log("Hero Name New value", newValue.heroName)
            },{
                deep: true
            })

            return {
                fName,
                lName,
                ...toRefs(state),
                ...toRefs(profile)
            }
        }
        
    
    }
</script>

<style scoped>

</style>