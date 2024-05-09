<template>
  <div>
    <h1>Student List Page</h1>
    <v-card>
      <v-data-table
        :headers="headers"
        :items="desserts"
        :items-per-page="5"
        class="elevation-1"
      ></v-data-table>
    </v-card>
  </div>
</template>
<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "Student #",
          align: "start",
          sortable: false,
          value: "student_no",
        },
        { text: "Lastname", value: "last_name" },
        { text: "Firstname", value: "first_name" },
        { text: "Middlename", value: "middle_name" },
        { text: "Course", value: "course" },
        { text: "Section", value: "section" },
      ],
      desserts: []
    };
  },
};
</script>