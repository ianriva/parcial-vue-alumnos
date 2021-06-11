<template>
  <div>
    <h1>{{ student.alumno }}</h1>
    <p>Legajo: {{ student.legajo }}</p>
    <ul v-for="nota in student.notas" :key="nota">
        <li>{{nota}}</li>
    </ul>
    <img src="" alt="" />
  </div>
</template>
<script>
export default {
  name: "StudentDetail",
  mounted() {
    this.getStudent();
  },
  data() {
    return {
      student: {},
    };
  },
  methods: {
    async getStudent() {
      const res = await fetch("http://localhost:8080/test/td/alumnos.json");
      const resJson = await res.json();
      const buscado = this.$route.params.id;
      this.student = resJson.filter((aux) => aux.legajo === buscado);
      
    },
  },
};
</script>