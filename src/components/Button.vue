<template>
    <button @click="onClick" >{{ title }}</button> 
</template>

<script>

export default {
    name: 'Button',
    props: {
        title: String,
        color: String,
        onClick: Function,
    },
}
    
</script>