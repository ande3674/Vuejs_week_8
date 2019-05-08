<template>  
    <tr>
        <td>{{student.name}}</td>
        <td>{{student.starID}}</td>
        <td><input type="checkbox" v-model="student.present" v-on:change="checked(student)"></td>
        <td v-show="edit">
            <img class="delete-icon" v-on:click="deleteStudent(student)" src="@/assets/cancel.png">    
        </td>
    </tr>
</template>

<script>
    // Create and export component here
    export default {
        name: 'StudentRow',
        props: {
            student: Object,
            edit: Boolean
        },
        methods: {
            checked(student) {
                this.$emit('student-present', student)
            },
            deleteStudent(student) {
                if (confirm(`Delete ${student.name}?`)) {
                    this.$emit('delete-student', student)
                }
            }
        }
    }
</script>

<style>
    /* Write styles for this component here */
    .present-true {
        color: gray;
        font-style: italic;
    }
    .present-false {
        font-weight: bold;
    }
</style>