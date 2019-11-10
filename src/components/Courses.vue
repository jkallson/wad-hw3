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
        <CourseAddition
                :courses="courses" :grades="grades" :calcGPA="calcGPA"
        />
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
                    new Course("Data Science",3,2),
                ],
                grades: [
                    82,
                    85,
                    99,
                    65,
                    2
                ],
            }

        },

        methods:{
            calcGPA() {
                let GPA = 0;
                for (let i = 0; i < this.grades.length ; i++) {
                    if(this.grades[i] > 90){
                        GPA = GPA + 4
                    }
                    if(this.grades[i] > 80 && this.grades[i] <= 90){
                        GPA = GPA + 3
                    }
                    if(this.grades[i] > 70 && this.grades[i] <= 80){
                        GPA = GPA + 2
                    }
                    if(this.grades[i] > 60 && this.grades[i] <= 70){
                        GPA = GPA + 1
                    }
                    if(this.grades[i] > 50 && this.grades[i] <= 60){
                        GPA = GPA + 0.5
                    }
                    if(this.grades[i] <= 50){
                        GPA = GPA + 0
                    }
                }
                let finalGPA = GPA / this.grades.length;
                finalGPA = finalGPA.toFixed(2);
                this.profile.gpa = finalGPA;
            }
        },

        beforeMount() {
            this.calcGPA()
        },

        props:{
            profile: Object
        }
    }
</script>

<style scoped>

</style>