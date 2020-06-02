<template>
  <div class="hello">
    <table>
      <thead>
        <tr>
          <th>Code</th>
          <th>Name</th>
          <th>Description</th>
          <th>Category</th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.name" v-for="item in filteredData">
          <td>{{ item.code }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.category }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    data: Array,
    filterKey: String, //name or description
    filterCategory: String,
    msg: String
  },
  /* data() {
    return {
      list: [
        {
          code: 1,
          name: "Cien Años de Soledad",
          description: "Novela legendaria",
          category: "Books"
        },
        {
          code: 2,
          name: "El Señor de los Anillos",
          description: "Novela de ciencia ficción",
          category: "Books"
        },
        {
          code: 3,
          name: "Un mundo feliz",
          description: "Novela metafórica",
          category: "Books"
        },
        {
          code: 4,
          name: "Orgullo y Prejuicio",
          description: "Novela",
          category: "Books"
        },
        {
          code: 5,
          name: "Ulises",
          description: "Novela contemporánea",
          category: "Books"
        },
        {
          code: 6,
          name: "Vogue",
          description: "Revista de moda y nuevas tendencias",
          category: "Magazines"
        },
        {
          code: 7,
          name: "Time",
          description: "Revista de polémica",
          category: "Magazines"
        },
        {
          code: 8,
          name: "Food Network Magazine",
          description: "Revista de alimentación, cocina y alta gastronomía",
          category: "Magazines"
        },
        {
          code: 9,
          name: "Fortune",
          description: "Revista global de negocios",
          category: "Magazines"
        },
        {
          code: 10,
          name: "Forbs",
          description: "Revista especializada en negocios y finanzas",
          category: "Magazines"
        },
        {
          code: 11,
          name: "The New York Times",
          description: "Periódico Estadounidense",
          category: "Newspapers"
        },
        {
          code: 12,
          name: "The Washington Post",
          description: "Periódico Estadounidense",
          category: "Newspapers"
        },
        {
          code: 13,
          name: "Los Tiempos",
          description: "Periódico Boliviano",
          category: "Newspapers"
        },
        {
          code: 14,
          name: "Opinión",
          description: "Periódico Boliviano",
          category: "Newspapers"
        },
        {
          code: 15,
          name: "Clarín",
          description: "Periódico Argentino",
          category: "Newspapers"
        },
        {
          code: 16,
          name: "El pequeño Larousse",
          description: "Enciclopedia",
          category: "Others"
        },
        {
          code: 17,
          name: "La Santa Biblia",
          description: "Biblia Latioamericana",
          category: "Others"
        },
        {
          code: 18,
          name: "Student's",
          description: "Richmond Dictionary",
          category: "Others"
        },
        {
          code: 19,
          name: "Iter Sopena",
          description: "Diccionario de español",
          category: "Others"
        },
        {
          code: 20,
          name: "Fábulas de Esopo",
          description: "Fábula infantil",
          category: "Others"
        }
      ]
    };
  },
};*/
  computed: {
    filteredData() {
      var filterKey = this.filterKey && this.filterKey.toLowerCase();
      return this.data.filter(
        item =>
          ((item.name.toLowerCase().includes(filterKey) ||
            item.description.toLowerCase().includes(filterKey)) &&
            item.category === this.filterCategory) ||
          (this.filterCategory === "All" &&
            (item.name.toLowerCase().includes(filterKey) ||
              item.description.toLowerCase().includes(filterKey)))
      );
    }
  }
};
</script>

<style src="../views/home.css" scoped></style>
