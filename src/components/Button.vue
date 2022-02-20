<template>
    <button @click="onClick" @dblclick="onDelete" >{{ title }}</button> 
</template>

<script>

export default {
    name: 'Button',
    props: {
        title: String,
        color: String
    },
    methods: {
        onClick() {
            this.$emit('click-event')
        },
        onDelete() {
            this.$emit('delete-grocery')
        }
    }
}
    
</script>