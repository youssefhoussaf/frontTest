<template>

    <div class="container mt-4">

        <div>
            <div class="form-group">
                <label for="exampleInputEmail1">Name</label>
                <input type="text" class="form-control" placeholder="Enter name">
            </div>
            <div class="form-group">
                <label for="exampleInputEmail1">Price</label>
                <input type="number" class="form-control" placeholder="Enter price">
            </div>
            <div class="form-group">
                <label for="exampleInputEmail1">Qte</label>
                <input type="number" class="form-control" placeholder="Enter qte">
            </div>
            <button type="submit" class="btn btn-primary mt-2">Submit</button>
        </div>

    </div>

</template>


<script>


export default {
    name: 'NewProcuct',
    data: function () {
        return {
        }
    },
    methods: {
    }
}


</script>

<style>

.form-group {
    margin-bottom: 1rem;
}

</style>