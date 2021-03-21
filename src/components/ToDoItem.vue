<template>
<div>
    <input type="checkbox" :id="id" :checked="isDone" >
    <label :for="id"> {{label}} </label>
</div>

</template>

<script>
    export default {
        props: {
            id: {required: true, type: String},
            label: {required: true, type: String},
            done: {default: false, type: Boolean}
        },
        data() {
            return {
                isDone: this.done,
            }
        }
    };
</script>