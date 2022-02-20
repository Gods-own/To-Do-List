<template>
    <div>
        <p>{{grocery.text}}</p>
        <Button @delete-grocery="$emit('delete-grocery', grocery.id)" title='X'/>
    </div>
</template>

<script>
import Button from './Button'

export default {
    name: "Grocery",
    props: {
        grocery: Object
    },
    components: {
        Button
    },
    emits: ['delete-grocery']
}
</script>