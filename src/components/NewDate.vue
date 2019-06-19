<template>
    <div>
        <input 
            type="date" 
            ref="input"
            :value="dateTo"
            @input="updateValue($event.target)"
            @focus="selectAll" 
        >
    </div>
</template>

<script>
import { setTimeout } from 'timers';
    export default {
        props: {
            value: {
                type: Date,
                default: new Date()
            },
        },
        methods: {
            dateTo(e) {
                return e && e.toISOString().split('T')[0]
            },
            updateValue(target){
                this.$emit('input', target.valueAsDate)
            },
            selectAll(event){
                setTimeout(function(){
                    event.target.select()
                },0)
            }
        },
    }
</script>

<style scoped>

</style>