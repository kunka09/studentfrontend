<template>
    <div>
        <b-modal id="editStudentModal" title="Student Entry" ok-title="Save" @ok="onSubmit">
            <form action="#">
                <b-form-group
                label="Name"
                label-for="name"
                >
                <b-form-input id="name" v-model="student.name" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Email"
                label-for="email"
                >
                <b-form-input id="author" v-model="student.author" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Address"
                label-for="address"
                >
                <b-form-input id="genre" v-model="student.genre" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Contact"
                label-for="contact"
                >
                <b-form-input id="publisher" v-model="student.publisher" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Birth Date"
                label-for="birthdate"
                >
                <b-form-input id="date_published" type="date" v-model="student.date_published" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Course"
                label-for="course"
                >
                <b-form-input id="pages" v-model="student.pages" trim></b-form-input>
                </b-form-group>

            </form>
        </b-modal>
    </div>
</template>
<script>
export default {
    props: {
        student: {}
    },
    methods: {
        async onSubmit() {
            this.$axios.put('http://127.0.0.1:8000/api/students/'+this.student.id, this.student)
                .then((res)=>{
                    if(res.status==202) {
                        alert('Update successfully!!')
                    }
                })
                .catch((err)=> {
                    alert(err.message)
                })
        }
    }
}
</script>