<template>
    <div>
        <!-- Write template here -->
        <div class="card student-list m-2 p-2">
          <h4 class="card-title">Students</h4>

          <div class="edit-table-toggle form-check">
              <input type="checkbox" id="edit-table" class="form-check-input" v-model="editTable">
              <label for="edit-table" class="form-check-label">Edit table?</label>
          </div>
          <div id="student-table">
              <table class="table">
                  <tr>
                      <th>Name</th>
                      <th>StarID</th>
                      <th>Present?</th>
                      <th v-show="editTable">Delete</th>
                  </tr>
                  <!-- create table rows
                  Each row will have a checkbox, bound to the app data
                  When the checkbox is checked/unchecked, the student will be signed in/out
                   -->
                   <StudentRow
                        v-for="student in students" v-bind:key="student.name"
                        v-bind:student="student"
                        v-bind:edit="editTable"
                        v-on:student-present="studentArrivedOrLeft"
                        v-on:delete-student="studentDeleted">
                   </StudentRow>
              </table>
          </div>
      </div>
    </div>
</template>

<script>
    // Create and export component here
    import StudentRow from '@/components/StudentRow.vue'
    
    export default {
        name: 'StudentTable',
        components: { StudentRow },
        data() {
            return {
                editTable: false
            }
        },
        props: {
            students: Array
        },
        methods: {
            studentArrivedOrLeft(student) {
                this.$emit('student-present', student)
            },
            studentDeleted(student) {
                this.$emit('delete-student', student)
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