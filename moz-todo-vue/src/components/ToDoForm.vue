<template>
    <form v-on:submit.prevent = "onSubmit">
        <label for = "new-todo-input"> What needs to be done? </label>
        <input
            type = "text"
            id = "new-todo-input"
            name = "new-todo"
            autocomplete = "off" 
            v-model.lazy.trim = "label" />
        <button type = "submit">Add</button>
    </form>
</template>

<script>
    export default {
        methods: {
            onSubmit() {
                console.log("Form Submitted.");
                if (this.label === "") {
                    return;
                }
                console.log("- Label Value: ", this.label);
                this.$emit("todo-added", this.label);
                this.label = "";
            },
        },
        data() {
            return {
                label: "",
            };
        },
    };
</script>