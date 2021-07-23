<template>
    <div>
        <b-modal id="deleteStudentModal" title="Student Entry" ok-title="Delete Student" @ok="onDelete" ok-variant="danger">
            Are you sure you want to delete this student? <br>
            {{student.name}} <br> {{student.email}}
        </b-modal>
    </div>
</template>
<script>
export default {
    props: {
        student: {}
    },
    methods: {
        async onDelete() {
            this.$axios.delete('http://127.0.0.1:8000/api/students/'+this.student.id)
            .then((res)=>{
                if(res.status==202) {
                    alert('Student deleted')
                    this.$emit('onDeleted')
                }
            })
        }
    }
}
</script>
