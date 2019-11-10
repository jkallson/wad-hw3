<template>
    <div>
        <button @click="toggleVisibility" id="add-course-button" class="blue-button">+</button>
        <span v-if="this.isVisible" id="add-course">
            <input v-model="courseValue" class="input" type="text" placeholder="Course title" id="title">
            <input v-model="semesterValue" class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input v-model="gradeValue" class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button @click="saveCourse" class="green-button" id="save-course">Save</button>
            <button @click="toggleVisibility" class="grey-button" id="cancel-course">Cancel</button>
        </span>

    </div>
</template>

<script>

    import Course from "../models/Course";

    export default {
        name: "CourseAddition",


        data: () => {
            return{
                isVisible: false,
                courseValue: "",
                semesterValue: 0,
                gradeValue: 0
            }
        },


        methods: {
            toggleVisibility() {
                this.isVisible = !this.isVisible;
            },

            saveCourse() {

                const course = new Course(this.courseValue,this.semesterValue,this.gradeValue);
                this.grades.push(this.gradeValue);
                this.courses.push(course);
                this.courseValue = "";
                this.semesterValue = 0;
                this.gradeValue = 0;
                this.toggleVisibility();
                this.calcGPA();
            }

        },

        props: {
            courses: Array,
            grades: Array,
            calcGPA: Function
        }
    }
</script>

<style scoped>
    #add-course {
    }

</style>