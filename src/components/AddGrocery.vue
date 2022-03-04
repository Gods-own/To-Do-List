<template>
    <form  @submit="submitGrocery">
        <div>
            <input type="text" v-model="text" name="grocery">
        </div>
        <div>
            <Button title='Submit Here'/>
        </div>
    </form>
</template>

<script>
import Button from './Button'

export default {
    name: 'AddGrocery',
    components: {
        Button
    },
    data() {
        return {
            text: ''
        }
    },
    methods: {
        submitGrocery(e) {
            e.preventDefault();

            if(!this.text) {
                alert('Please add an item')
                return
            }

            const newGrocery = {
                id: Math.floor(Math.random() * 10000),
                text: this.text
            }

            this.text = ''

            this.$emit('addgrocery', newGrocery)
        } 
    },
    emits: ['addgrocery']
}
</script>