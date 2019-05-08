<template>  
    <tr>
        <td>{{student.name}}</td>
        <td>{{student.starID}}</td>
        <td><input type="checkbox" v-model="student.present" v-on:change="checked(student)"></td>
    </tr>
</template>

<script>
    // Create and export component here
    export default {
        name: 'StudentTable',
        props: {
            students: Object
        },
        methods: {
            checked(student) {
                this.$emit('student-present', student)
            }
        }
    }
</script>

<style>
    /* Write styles for this component here */

</style>