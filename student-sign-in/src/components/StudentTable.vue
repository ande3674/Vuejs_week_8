<template>
    <div>
        <!-- Write template here -->
        <div class="card student-list m-2 p-2">
          <h4 class="card-title">Students</h4>
          <div id="student-table">
              <table class="table">
                  <tr>
                      <th>Name</th>
                      <th>StarID</th>
                      <th>Present?</th>
                  </tr>
                  <!-- create table rows
                  Each row will have a checkbox, bound to the app data
                  When the checkbox is checked/unchecked, the student will be signed in/out
                   -->
                   <tr v-for="student in students" v-bind:class="'present-' + student.present">
                     <td>{{student.name}}</td>
                     <td>{{student.starID}}</td>
                     <td><input type="checkbox" v-model="student.present" v-on:change="checked(student)"></td>
                   </tr>
              </table>
          </div>
      </div>
    </div>
</template>

<script>
    // Create and export component here
    export default {
        name: 'StudentTable',
        props: {
            students: Array
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
    #student-table {
        max-height: 500px;
        overflow: scroll;
    }

    .present-true {
        color: gray;
        font-style: italic;
    }

    .present-false {
        font-weight: bold;
    }

</style>