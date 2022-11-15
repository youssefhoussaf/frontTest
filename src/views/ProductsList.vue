<template>

    <div class="container mt-4">

        <h1>Products</h1>

        <div class="mb-4">
            <div class="form-group">
                <label for="exampleInputEmail1">Name</label>
                <input type="text" class="form-control" placeholder="Enter name" v-model="form.name">
            </div>
            <div class="form-group">
                <label for="exampleInputEmail1">Price</label>
                <input type="number" class="form-control" placeholder="Enter price" v-model="form.price">
            </div>
            <div class="form-group mb-4">
                <label for="exampleInputEmail1">Qte</label>
                <input type="number" class="form-control" placeholder="Enter qte" v-model="form.qte">
            </div>
            <button type="submit" class="btn btn-primary mx-2" @click="submit()">Submit</button>
            <button type="submit" class="btn btn-secondary mx-2" @click="cancel()">Cancel</button>
        </div>

        <table class="table">
            <thead class="thead-dark">
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Name</th>
                    <th scope="col">Price</th>
                    <th scope="col">Qte</th>
                    <th scope="col"></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="d of data">
                    <th scope="row">{{d.id}}</th>
                    <td>{{d.name}}</td>
                    <td>{{d.price}}</td>
                    <td>{{d.qte}}</td>
                    <td>
                        <button @click="updateProduct(d)" class="action_btn mx-2 text-primary">
                            <font-awesome-icon :icon="faTrash" />
                        </button>
                        <button @click="deleteProduct(d.id)" class="action_btn mx-2 text-danger">
                            <font-awesome-icon :icon="faPenToSquare" />
                        </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>

</template>


<script>

import { faTrash, faPenToSquare } from '@fortawesome/free-solid-svg-icons'

import axios from 'axios'

export default {
    name: 'Procucts',
    data: function () {
        return {
            faTrash: faTrash,
            faPenToSquare: faPenToSquare,
            data: [],
            form:{
                id: null,
                name: null,
                price: null,
                qte: null,
            }
        }
    },
    mounted(){
        this.load();
    },
    methods: {
        load(){
            axios.get('http://127.0.0.1:8000/api/getProducts').then(response=>{
            if(response.data.success){
                this.data = response.data.data;
            }
        });
        },
        submit(){
            if(this.form.id==null){
                axios.post('http://127.0.0.1:8000/api/addProduct',this.form).then(response=>{
                    if(response.data.success){
                        this.load();
                        this.cancel();
                    }
                });
            }
            else{
                axios.post('http://127.0.0.1:8000/api/updateProduct',this.form).then(response=>{
                    if(response.data.success){
                        this.load();
                        this.cancel();
                    }
                });
            }
        },
        deleteProduct(id){
            axios.post('http://127.0.0.1:8000/api/deleteProduct',{id}).then(response=>{
                if(response.data.success){
                    this.load();
                    this.cancel();
                }
            });
        },
        updateProduct(product){
            if(this.form.id==product.id){this.cancel();return;}
            this.form={
                id: product.id,
                name: product.name,
                price: product.price,
                qte: product.qte,
            }
        },
        cancel(){
            this.form={
                id: null,
                name: null,
                price: null,
                qte: null,
            }
        },
    }
}


</script>

<style>
.thead-dark th {
    color: #fff;
    background-color: #212529;
    border-color: #32383e;
}

.action_btn{
    background-color: transparent;
    border: 0;
}
</style>