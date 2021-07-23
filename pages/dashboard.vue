<template>
    <div>
        <NavBar />
        <div class="container">
            <br>
            <h1>Dashboard</h1>
            <table class="table table-striped">
            <thead>
                <tr class="bg-info text-white">
                    <th>ID</th>
                    <th>Name</th>
                    <th>Email</th>
                </tr>
            </thead>
            <tbody>
                <td>{{$auth.user.id}}</td>
                <td>{{$auth.user.name}}</td>
                <td>{{$auth.user.email}}</td>
            </tbody>
                <tr><td><a class="btn btn-primary btn-lg btn-block" href="/students" role="button">Students</a></td></tr>  
            </table>
        </div>
    </div>
</template>
