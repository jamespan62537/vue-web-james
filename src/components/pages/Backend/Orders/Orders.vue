<template>
  <div class="orders-area">
    <v-data-table
      class="elevation-1 table"
      :headers="headers"
      :items="items"
      :items-per-page="10"
      item-key="id"
      style="background-color: rgb(255, 255, 255);"
      hide-default-footer
    >
      <template v-slot:item.products="{ item }">
        <li v-for="product in item.products" :key="product.id">{{product.product.title}}</li>
      </template>
      <template v-slot:item.is_paid="{ item }">
        <p v-if="item.is_paid">已付款</p>
        <p v-else>未付款</p>
      </template>
    </v-data-table>
    <Pagination :pages="pagination" @callPage="getOrders"></Pagination>
  </div>
</template>

<script>
import $ from "jquery";
import Pagination from "../../../Pagination.vue";
export default {
  data: function() {
    return {
      headers: [
        {
          text: "買家",
          value: "user.name",
          class: "teal--text darken-1"
        },
        {
          text: "Email",
          value: "user.email",
          class: "teal--text darken-1",
          sortable: false
        },
        {
          text: "購買品項",
          value: "products",
          class: "teal--text darken-1",
          sortable: false
        },
        {
          text: "應付金額",
          value: "total",
          class: "teal--text darken-1",
          sortable: false
        },
        {
          text: "是否付款",
          value: "is_paid",
          class: "teal--text darken-1",
          sortable: false
        }
      ],
      items: [],
      products: [],
      pagination: {}
    };
  },
  components: {
    Pagination
  },
  methods: {
    getOrders: function(page = 1) {
      var vm = this;
      vm.$store.dispatch("updateLoading", true);
      // /api/:api_path/admin/orders?page=:page
      const api = `${process.env.VUE_APP_API}/admin/orders?page=${page}`;
      this.$http.get(api).then(response => {
        if (response.data.success) {
          vm.$store.dispatch("updateLoading", false);
          vm.items = response.data.orders;
          vm.pagination = response.data.pagination;
        }
      });
    }
  },
  created() {
    this.getOrders();
  }
};
</script>