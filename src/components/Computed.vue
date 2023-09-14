<template>
    <div>
        <h1>Options API using v-model directive</h1>
        <input type="text" placeholder="First name" v-model="fName" />
        <input type="text" placeholder="Last name" v-model="lName" />
        <h2>Options Full name is {{ fullname }}</h2>
    </div>
</template>

<script>
    export default {
        name: "Computed",

        data() {
            return {
                fName: '',
                lName: '',
            }
        },
        computed: {
            fullname() {
                return `${this.fName} ${this.lName}`
            }
        }
    }
</script>

<style scoped>

</style>