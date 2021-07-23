<template>
    <div>
        <NavBar />
        <EditStudentModal :student="selectedStudent" />
        <DeleteStudentModal :student="selectedStudent" @onDeleted="getAll"/>
        <div class="container">
            <h1>
                Students
                <StudentEntryModal class="float-right" @onAdd="getAll"/>
            </h1>

            <table class="table table-bordered table-stripped">
                <thead>
                    <tr class="bg-info text-white">
                        <th>ID</th>
                        <th>Name</th>
                        <th>Email</th>
                        <th>Address</th>
                        <th>Contact</th>
                        <th>Date Birth</th>
                        <th>Course</th>
                        <th>&nbsp;</th>
                        <th>&nbsp;</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="student in students" :key="student.id">
                        <td>{{student.id}}</td>
                        <td>{{student.name}}</td>
                        <td>{{student.email}}</td>
                        <td>{{student.address}}</td>
                        <td>{{student.contact}}</td>
                        <td>{{student.birthdate}}</td>
                        <td>{{student.course}}</td>
                        <td>
                            <b-button @click="onEdit(student)" variant="info" size="sm">
                                Edit
                            </b-button>
                        </td>
                        <td>
                            <b-button @click="onDelete(student)" variant="danger" size="sm">
                                Delete
                            </b-button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            students: [],
            selectedStudent: {}
        }
    },
    methods: {
        async getAll() {
            await this.$axios.get('https://lentrix.tk/jim/api/students')
            .then((res)=>{
                if(res.status==200) {
                    this.students =res.data
                }
            })
        },
        onEdit(selectedStudent) {
            this.selectedStudent = selectedStudent;
            this.$bvModal.show('editStudentModal')
        },
        onDelete(selectedStudent) {
            this.selectedStudent = selectedStudent;
            this.$bvModal.show('deleteStudentModal')
        }
    },
    created() {
        this.getAll()
    }
}
</script>