<template>
    <div>
        <input type="checkbox" v-model="model" @change="$emit('input', model)"/>
    </div>
</template>
<script>
export default {
    name: 'CheckboxCompoent',
    data(){
        return{
            model: false
        }
    }
}
</script>
<style scoped>

</style>