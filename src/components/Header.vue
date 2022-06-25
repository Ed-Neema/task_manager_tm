<template>
    <header>
        <h1>
            {{title}}
        </h1>
        <ButtonComponent @btn-click="$emit('toggle-add-task')"  :btnTitle="showAddTask ? 'Close': 'Add Task'" :color="showAddTask ? 'red': 'green'" />
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
        },
        showAddTask: Boolean
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