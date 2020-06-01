<template>
  <div class="hello">
    <table>
      <thead>
        <tr>
          <th
            :key="columnkey"
            v-for="columnkey in columns"
            :class="{ active: sortKey == columnkey }"
          >
            {{ columnkey }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.data" v-for="item in filteredData">
          <td :key="key" v-for="key in columns">
            {{ item[key] }}
          </td>
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
    columns: Array,
    filterKey: String, //name or description
    filterCategory: String,
    msg: String
  },
  data() {
    var sortOrders = {};
    this.columns.forEach(function(key) {
      sortOrders[key] = 1;
    });
    return {
      sortKey: "",
      sortOrders: sortOrders
    };
  },
  computed: {
    filteredData() {
      var filterKey = this.filterKey && this.filterKey.toLowerCase();
      var filterCategory =
        this.filterCategory && this.filterCategory.toLowerCase();
      var data = this.data;
      if (filterCategory === "All") {
        filterKey = "";
      } else if (filterKey && filterCategory != "All") {
        data = data.filter(function(row) {
          return Object.keys(row).some(function(key) {
            return (
              String(row[key])
                .toLowerCase()
                .indexOf(filterKey && filterCategory) > -1
            );
          });
        });
      }
      return data;
    }
  }
};
</script>

<style src="../views/home.css" scoped></style>
