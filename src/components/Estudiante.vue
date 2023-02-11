<template >
    <div>
        <input v-model="idBuscar" type="text" />
        <button v-on:click="buscar()">Buscar</button>
        <h1>ID: {{ idEstudiante }}</h1>
        <h1>Nombre: {{ nombre }}</h1>
        <h1>Apellido: {{ apellido }}</h1>
        <h1>Fecha nacimiento: {{ fechaNacimiento }}</h1>
        <h1>Salario: {{ salario }}</h1>
    </div>
</template>
<script>
export default {
    data() {
        return {
            idBuscar: null,
            idEstudiante: null,
            nombre: null,
            apellido: null,
            fechaNacimiento: null,
            salario: null,
        }
    },
    methods: {
        async buscar() {
            const { id, nombre, apellido, fechaNacimiento, salario } = await this.consumirAPI(this.idBuscar)
            this.idEstudiante = id
            this.nombre = nombre
            this.apellido = apellido
            this.fechaNacimiento = fechaNacimiento
            this.salario = salario
        },
        async consumirAPI(idEstu) {
            const data = await fetch("http://localhost:8085/API/Matricula/V1/estudiantes/" + idEstu + "").then((r) => r.json())
            return data
        }
    },
}
</script>
<style >

</style>