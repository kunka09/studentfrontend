<template>
  <div>
    <NavBar />
    <div class="container">
      <div class="card">
        <div class="card-header">
          <h1>Welcome to Our Page</h1>
        </div>
      </div>
      <div class="card">
        <div class="card-header">
          <span><b>Here you can put all the students that are enrolled.
            <template v-if="$auth.loggedIn">
              <a href="/dashboard">click here</a>
            </template>

            <template v-else>
              <a href="/login">click here</a>
            </template>
          </b></span>
        </div>
        
      </div>
      <div class="background-image">
        <figure v-for="{image, i} in images" :key="i">
            <img class="w-auto rounded-lg mx-auto p-2" :src="`~/assets/{{image}}.jpg`">
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      images: ['background']
    }
  },
  auth: false
}
</script>
<style scoped>
.card{
  margin: 20px;
  margin-top: 20px;
}
.background-image {
  margin: 20px;
  padding: 350px;
  background: url('~/assets/background.jpg');
}
</style>