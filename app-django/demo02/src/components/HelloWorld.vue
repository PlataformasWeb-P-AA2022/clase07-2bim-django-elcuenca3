<template>
    <div class="tasks_container">
        <div class="tasks_content">
            <h1>Listado de Estudiantes</h1>
            <!--ul class="tasks_list"-->
                <span v-for="telefono in tasks" :key="telefono.id">
                    <p><b>Telefono:</b> {{ telefono.telefono }}</p>
                    <p><b>Tipo:</b>{{ telefono.tipo }}</p>
                    <hr>
                </span>
            <!--/ul-->
        </div>
    </div>
  <hr>
   
</template>

<script>
    export default {
        data() {
            return {
                // tasks
                tasks: [''],
                telefono: '',
                tipo: '',
            }
        },
        methods: {
            async getData() {
                try {
                    // fetch tasks
                    const response = await this.$http.get('http://localhost:8000/api/numerost/');
                    // set the data returned as tasks
                    this.tasks = response.data;
                } catch (error) {
                    // log the error
                    console.log(error);
                }
            }
        },
        created() {
            // Fetch tasks on page load
            this.getData();
        }
    }
</script>