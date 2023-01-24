<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <form-component></form-component>
                <thought-component 
                v-for="thought in thoughts" 
                :key="thought.id"
                :thought="thought">
            </thought-component>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            thoughts: [{
                'id': 1,
                'description': 'abc',
                'created_at': '24/01/2023'
            }]
        }
    },
    mounted() {
        console.log('Component mounted.')
    }
}
</script>
