<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12">
      <div class="text-center">
        <v-subheader>
          <h2>{{ subject }}</h2>
        </v-subheader>
        <v-simple-table>
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">Titel</th>
                <th class="text-left">Datum</th>
                <th class="text-left">Note</th>
                <th class="text-left">Gewichtung</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in grades" :key="item.name">
                <td class="text-left">{{ item.title }}</td>
                <td class="text-left">{{ item.date }}</td>
                <td class="text-left">{{ item.grade }}</td>
                <td class="text-left">{{ item.weight }}</td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
        <v-divider></v-divider>
        <v-subheader>
          <h2>Durchschnitt: {{ getAverageGrade() }}</h2>
        </v-subheader>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      subject: 'Programmieren',
      grades: [
        {
          title: 'Grundlagen',
          date: '12.11.2020',
          grade: '6.0',
          weight: '1.0',
        },
        {
          title: 'Funktionen',
          date: '12.11.2020',
          grade: '4.5',
          weight: '1.0',
        },
        {
          title: 'Arrays',
          date: '12.11.2020',
          grade: '5.5',
          weight: '1.0',
        },
      ],
    }
  },
  methods: {
    getAverageGrade() {
      this.total = 0
      this.gradesAmount = 0
      this.grades.forEach((grade) => {
        this.total += parseFloat(grade.grade)
        this.gradesAmount++
      })

      return Math.round(this.total / this.gradesAmount)
    },
  },
}
</script>
