<template>
    <div>
        <h2>{{ name }}</h2>
    </div>
</template>

<script>
import { reactive, toRefs } from 'vue';
    export default {
        name: "DemoTwo",
         setup() {
            const state = reactive({
                name: 'John',
            })

            setTimeout(() => {
                state.name = 'Jane'
            }, 2000)

            return toRefs(state)

         }
    }
</script>

<style lang="scss" scoped>

</style>