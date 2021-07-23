<template>
    <div>
        <b-button v-b-modal.studentEntryModal variant="primary" class="float-right mt-2">Add Student</b-button>
        <b-modal id="studentEntryModal" title="Add Student" ok-title="Save" @ok="onSubmit">
            <form action="#">
                <b-form-group
                label="Name"
                label-for="name"
                >
                <b-form-input id="name" v-model="students.name" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Email"
                label-for="email"
                >
                <b-form-input id="email" v-model="students.email" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Address"
                label-for="address"
                >
                <b-form-input id="address" v-model="students.address" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Contact"
                label-for="contact"
                >
                <b-form-input id="contact" v-model="students.contact" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Birthdate"
                label-for="birthdate"
                >
                <b-form-input id="birthdate" type="date" v-model="students.birthdate" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Course"
                label-for="course"
                >
                <b-form-input id="course" v-model="students.course" trim></b-form-input>
                </b-form-group>

            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    data() {
        return {
            students: {}
        }
    },
    methods: {
        async onSubmit() {
            this.$axios.post('http://127.0.0.1:8000/api/students', this.students)
            .then((res)=>{
                if(res.status==202) {
                    alert('Student added successfully ')
                    this.$emit('onAdd')
                }
            })
        }
    }
}
</script>