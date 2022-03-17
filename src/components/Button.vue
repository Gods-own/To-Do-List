<template>
    <button @click="onClick($event)" :type="type" >
        <slot></slot>
    </button> 
</template>

<script>

export default {
    name: 'Button',
    props: {
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