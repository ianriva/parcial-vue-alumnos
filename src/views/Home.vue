<template>
  <div class="home">
    <StudentList />
  </div>
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Alumno</th>
        <th>Legajo</th>
        <th>Fecha Nac</th>
        <th>Promedio notas</th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="student in studentsData" :key="student.legajo">
        <td>{{ student.alumno }}</td>
        <td>{{ student.legajo }}</td>
        <td>{{ student.fechaNacimiento }}</td>
        <td>{{promedio(student.notas) }}</td>
        <td><router-link class="btn btn-primary btn-sm" :to="`/student/${student.legajo}`" >Detalle</router-link></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
// @ is an alias to /src
import StudentList from "@/components/StudentList.vue";

export default {
  name: "Home",
  components: {
    StudentList,
  },
  mounted() {
    this.getStudents();
  },
  data() {
    return {
      studentsData: [],
    };
  },
  methods: {
    async getStudents() {
      const res = await fetch("http://localhost:8080/test/td/alumnos.json");
      const resJson = await res.json();
      console.log(resJson);
      this.studentsData = resJson;
    },
    promedio (arr) {
      let suma = 0;
      for (let nota of arr ){
        suma += nota;
      }
      return suma/arr.length
    },
  },
};
</script>
