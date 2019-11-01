<template>
    <div>
        <button @click="toggleVisibility" id="add-course-button" class="blue-button">+</button>
        <span v-if="this.isVisible" id="add-course">
            <input class="input" type="text" placeholder="Course title" id="title">
            <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button class="green-button" id="save-course">Save</button>
            <button class="grey-button" id="cancel-course">Cancel</button>
        </span>
    </div>
</template>

<script>
    export default {
        name: "CourseAddition",

        data: () => {
            return{
                isVisible: false,
            }
        },
        methods: {
            toggleVisibility() {
                this.isVisible = !this.isVisible;
            }
        }
    }
</script>

<style scoped>
    #add-course {
    }

</style>