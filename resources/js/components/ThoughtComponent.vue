<template>
    <!--component to display the post-->
    <div class="container">
        <div class="card">
            <div class="card-header">Publicado en {{ thought.created_at }}</div>
            <div class="card-body">
                <div class="panel-body">
                    <input v-if="editMode"  type="text" class="form-control" v-model="thought.description">
                    <p v-else> {{ thought.description }}</p>
                </div>
                <div class="panel-footer">
                    <button v-if="editMode" class="btn btn-success" v-on:click="onClickUpdate">
                        Guardar cambios
                    </button>
                    <button v-else class="btn btn-default" v-on:click="onClickEdit">
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
    data() {
        return {
            editMode: false
        }
    },
    props: ['thought'],
    mounted() {
        console.log('post.' + this.thought.id)
    },
    methods: {
        onClickDelete() {
                axios.delete(`/thoughts/${this.thought.id}`).then(() => {
                    this.$emit('delete');
                });
            },
            onClickEdit() {
                this.editMode = true;
            },
            onClickUpdate() {
                const params = {
                    description: this.thought.description
                };
                axios.put(`/thoughts/${this.thought.id}`, params).then((response) => {
                    this.editMode = false;
                    const thought = response.data;
                    this.$emit('update', thought);
                });
            }
    }
}
</script>
