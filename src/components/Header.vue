<template>
    <header>
        <h1>
            {{title}}
        </h1>
        <ButtonComponent btnTitle="Add Task" color="green"/>
    </header>
</template>

<script>
import ButtonComponent from './Button'
export default {
    name: 'HeaderComponent',
    components: {
        ButtonComponent
    },
    props: {
        title: {
            type: String,
            default: "Hello world",
            required: false

        }
    }
}
</script>
<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>