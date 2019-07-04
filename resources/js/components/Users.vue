<template>
    <div>
        <section class="content">
            <div class="row justify-content-around">
                <div class="col-10">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">User List</h3>
                            <div class="card-tools">
                                <button class=" btn btn-info" data-toggle="modal" data-target="#exampleModal">Add Category</button>
                            </div>
                        </div>
                        <!-- /.card-header -->
                        <div class="card-body">
                            <table id="example2" class="table table-bordered table-hover">
                                <thead>
                                <tr>
                                    <th>Sl</th>
                                    <th>Name</th>
                                    <th>Email</th>
                                    <th>Type</th>
                                    <th>Action</th>
                                </tr>
                                </thead>
                                <tbody>
                                <tr>
                                    <td>1</td>
                                    <td>name</td>
                                    <td>email</td>
                                    <td>type</td>
                                    <td>
<!--                                        <router-link :to="`/edit-category/${category.id}`">Edit</router-link>-->
<!--                                        <a href="" @click.prevent="deleteCategory(category.id)" >Delete</a>-->
                                    </td>
                                </tr>
                                </tbody>
                            </table>
                        </div>
                        <!-- /.card-body -->
                    </div>
                </div>
                <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
                    <div class="modal-dialog modal-dialog-centered" role="document">
                        <div class="modal-content">
                            <div class="modal-header">
                                <h5 class="modal-title" id="exampleModalLabel">Add New User</h5>
                                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                    <span aria-hidden="true">&times;</span>
                                </button>
                            </div>
                            <form @submit.prevent="createUser" >
                            <div class="modal-body">
                                <div class="form-group">
                                    <input v-model="form.name" type="text" name="name" placeholder="Enter Your Name"
                                           class="form-control" :class="{ 'is-invalid': form.errors.has('name') }">
                                    <has-error :form="form" field="name"></has-error>
                                </div>
                                <div class="form-group">
                                    <input v-model="form.name" type="email" name="email" placeholder="Enter Email Address"
                                           class="form-control" :class="{ 'is-invalid': form.errors.has('email') }">
                                    <has-error :form="form" field="email"></has-error>
                                </div>
                                <div class="form-group">
                                    <input v-model="form.password" type="password" name="password" placeholder="Enter Password"
                                           class="form-control" :class="{ 'is-invalid': form.errors.has('password') }">
                                    <has-error :form="form" field="password"></has-error>
                                </div>
                                <div class="form-group">
                                    <select class="form-control"  name="cat_id" v-model="form.type" :class="{ 'is-invalid': form.errors.has('type') }">
                                        <option selected value="" >--Select Type--</option>
                                        <option value="" >Super Admin</option>
                                        <option value="" >Admin</option>
                                        <has-error :form="form" field="type"></has-error>
                                    </select>
                                </div>
                                <div class="form-group">
<!--                                    <input v-model="form.name" type="email" name="email" placeholder="Enter Email Address"-->
<!--                                           class="form-control" :class="{ 'is-invalid': form.errors.has('email') }">-->
                                    <textarea v-model="form.bio"  name="bio" class="form-control" :class="{ 'is-invalid': form.errors.has('bio') }" ></textarea>
                                    <has-error :form="form" field="bio"></has-error>
                                </div>
                            </div>
                            <div class="modal-footer">
                                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                                <button type="button" class="btn btn-primary">Save changes</button>
                            </div>
                            </form>
                        </div>
                    </div>
                </div>

            </div>
            <!-- /.row -->
        </section>
    </div>
</template>

<script>
    export default {
        data(){
          return {
              form: new Form({
                  username: '',
                  email: '',
                  password: '',
                  type:'',
                  bio: '',
                  photo: ''
              })
          }
        },
        methods:{
            createUser(){
                this.form.post('/api/add-user')
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
