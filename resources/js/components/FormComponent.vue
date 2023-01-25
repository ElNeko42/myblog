<template>
    <!-- form component to create a new post-->
    <div class="container">
        <div class="card">
            <div class="card-header">En que estás pensando?</div>

            <div class="card-body">
              
                <form action="" v-on:submit.prevent="newThought()">
                    <div class="form-group">
                        <label for="thought">Ahora estoy pensando en:</label>
                        <input type="text" class="form-control" name="thought" v-model="description">
                        <button type="submit" class="btn btn-primary">
                            Enviar pensamiento
                        </button>

                    </div>
                </form>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            description:''
        }
    },
    mounted() {
        console.log('Component post.')
    },
    methods:{
        newThought(){
            let thought ={
                id:2,
                description: this.description,
                created_at: '24/01/2023'
            }
            this.$emit('new',thought)
            //alert(this.description)
            this.description=''
        }
    }
}
</script>
