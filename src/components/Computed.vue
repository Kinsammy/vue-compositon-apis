<template>
    <div>
        <h1>Options API using v-model directive</h1>
        <input type="text" placeholder="First name" v-model="fName" />
        <input type="text" placeholder="Last name" v-model="lName" />
        <h2>Options Full name is {{ fullName }}</h2>
    </div>
    <div>
        <h1>Composition API using v-model directive, ref and computed function</h1>
        <input type="text" placeholder="First name" v-model="refFirstName" />
        <input type="text" placeholder="Last name" v-model="refLastName" />
        <h2>Ref Full name is {{ refFullName }}</h2>
    </div>

    <div>
        <h1>Compositio API using v-model directive, reactive, toRefs and computed function</h1>
        <input type="text" placeholder="First name" v-model="reactiveFirstName" />
        <input type="text" placeholder="Last name" v-model="reactiveLastName" />
        <h2>Reactiive Full name is {{ reactiveFullName }}</h2>
    </div>
</template>

<script>
import { ref, computed, reactive, toRefs } from "vue";
    export default {
        name: "Computed",

        data() {
            return {
                fName: '',
                lName: '',
            }
        },
        computed: {
            fullName() {
                return `${this.fName} ${this.lName}`
            }
        },

        // Compostion API
        setup() {
            // Using ref()
            const refFirstName = ref('')
            const refLastName = ref('')

            const refFullName = computed(function(){
                return `${refFirstName.value} ${refLastName.value}`
            })
            // Using reactive() and toRefs()
            const profile = reactive({
                reactiveFirstName: '',
                reactiveLastName: '',
            })

            const reactiveFullName = computed(function(){
                return `${profile.reactiveFirstName} ${profile.reactiveLastName}`
            })

            return {
                refFirstName,
                refLastName,
                refFullName,
                ...toRefs(profile),
                reactiveFullName,
            }
        }
    }
</script>

<style scoped>

</style>