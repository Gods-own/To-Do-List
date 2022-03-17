<template>
    <form  @submit.prevent="submitGrocery">
        <div>
            <input class="input" type="text" v-model="text" name="grocery">
        </div>
        <div>
            <Button class="button first">Submit Here</Button>
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
        submitGrocery() {
            if(!this.text) {
                alert('Please add an item')
                return
            }
            const newGrocery = {
                id: Math.floor(Math.random() * 10000),
                text: this.text
            }
            this.text = ''
            this.$emit('addGrocery', newGrocery)
        } 
    },
    emits: ['addGrocery']
}
</script>

<style scoped>
.input {
    border-style: none none solid none;
    outline: none;
    width: 350px;
    font-size: 20px;
}
</style>