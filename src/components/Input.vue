<template>
    <div>
        <input type="text" @input="$emit('input', $event.target.value)"/>
    </div>
</template>
<script>
export default {
    name:"InputComponent"
    
}
</script>
<style scoped>

</style>