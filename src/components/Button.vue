<template>
    <button class="btn" v-bind:style="{ background: color}">{{btnTitle}}</button>
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
    }
}
</script>