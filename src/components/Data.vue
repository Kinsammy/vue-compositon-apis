<template>
    <h2>
        Options - {{ o_firstName }}
    </h2>
    <h2>
        Composition - {{ c_firstName }}
    </h2> 
    <h2>
        reactive function - {{ personal.firstName }} {{ personal.lastName }}
    </h2> 
    <h2>
        reactive function - {{ greet }}
    </h2> 
</template> 

<script>
import { ref, reactive } from 'vue';
    export default {
        name: "Data",
        setup(){
            // ref function
            const c_firstName = ref("Samuel Fanu")

            // reactive function
            const personal = reactive({
                firstName: "Hannah",
                lastName: "Fanu"
            })
            const greet = `Hello ${personal.firstName} ${personal.lastName}`
            return {
                c_firstName,
                personal,
                greet
            }
        },
        data() {
            return {
                o_firstName: "Samuel"
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>