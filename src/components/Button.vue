<template>
    <button @click="onClick()" class="btn" v-bind:style="{ background: color}">{{btnTitle}}</button>
</template>

<script>

export default{
    name: 'ButtonComponent',
    props: {
        btnTitle: {
            required: true,
            type: String
        },
        color: {
            required: true,
            type: String
        }
    },
    methods: {
        onClick(){
            this.$emit('btn-click')
        }
    }
}
</script>