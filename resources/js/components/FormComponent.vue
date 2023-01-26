<template>
    <!-- form component to create a new post-->
    <div class="container">
        <div class="card">
            <div class="card-header">crear un nuevo post</div>

            <div class="card-body">
              
                <form action="" v-on:submit.prevent="newThought()">
                    <div class="form-group">
                        <label for="thought">escribe aqui tu nuevo post</label>
                        <input type="text" class="form-control " name="thought" v-model="description">
                        <button type="submit" class="btn btn-primary mt">
                            Enviar post
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
            const params = {
                description: this.description
            }
            axios.post('thoughts',params).then((response)=>{
                const thought =response.data
                this.$emit('new',thought)
            });
      
            this.$emit('new',thought)
            //alert(this.description)
            this.description=''
        }
    }
}
</script>
<style scoped>
.mt{
    margin-top:1em ;
}
</style>