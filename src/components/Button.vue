<template>
    <button @click="onClick($event)" :type="type" >{{ title }}</button> 
</template>

<script>

export default {
    name: 'Button',
    props: {
        title: String,
        color: String,
        type: String,
    },
    methods: {
        onClick(e) {
            e.stopImmediatePropagation()
            this.$emit('click', e)
        }
    }
}
    
</script>