<template>
    <div id="courses-container" class="tab">
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
            <tbody>
                <tr v-for="(course,index) in courses" :key="index">
                    <td>{{courses.indexOf(course)+1}}</td>
                    <td>{{course.title}}</td>
                    <td>{{course.semester}}</td>
                    <td>{{course.grade}}</td>
                </tr>
            </tbody>
        </table>
        <br>
        <br>
        <CourseAddition></CourseAddition>
    </div>
</template>

<script>
    import CourseAddition from "./CourseAddition";
    import Course from "../models/Course";
    export default {
        name: "Courses",
        components: {CourseAddition},
        data: () => {
            return{
                courses: [
                    new Course("Agile software development",1,82),
                    new Course("System modelling",1,85),
                    new Course("Object-oriented programming",2,99),
                    new Course("Estonian language Level A2",2,65),
                    new Course("Data Science",3,2)
                ]
            }
        }
    }
</script>

<style scoped>

</style>