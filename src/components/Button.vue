<template>
    <button @click.self="onClick($event)" :type="type" >{{ title }}</button> 
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
            this.$emit('click', e)
        }
    }
}
    
</script>