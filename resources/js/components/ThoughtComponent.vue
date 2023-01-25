<template>
    <!--component to display the post-->
    <div class="container">
        <div class="card">
            <div class="card-header">Publicado en {{ thought.created_at }}</div>
            <div class="card-body">
                <div class="panel-body">
                    <p>
                        {{ thought.description }}
                    </p>
                </div>
                <div class="panel-footer">
                    <button class="btn btn-default">
                        Editar
                    </button>
                    <button class="btn btn-danger" v-on:click="onClickDelete">
                        Eliminar
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['thought'],
    mounted() {
        console.log('post.'+this.thought.id)
    },
    methods:{
        onClickDelete(){
            this.$emit('delete')
        }
    }
}
</script>
