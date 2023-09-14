<template>
    <div>
        <h1>Options API using v-model directive</h1>
        <input type="text" placeholder="First name" v-model="fName" />
        <input type="text" placeholder="Last name" v-model="lName" />
    </div>
    <div>
        <h1>Composition API using v-model directive</h1>
        <input type="text" placeholder="Hero name" v-model="heroName" />
        <input type="text" placeholder="First name" v-model="firstName" />
        <input type="text" placeholder="Last name" v-model="lastName" />

    </div>
</template>

<script>
import {ref, reactive, toRefs} from 'vue'
    export default {
        name: "VModel",
        data() {
            return {
                fName: '',
                lName: '',
            }
        },
        setup() {
            const heroName = ref('')
            const state = reactive({
                firstName: '',
                lastName: '',
            })
            return {
                heroName,
              ...toRefs(state)
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>