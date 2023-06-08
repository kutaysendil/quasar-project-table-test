<template>
  <q-page>
    <q-grid
      :data="data"
      :columns="columns"
      :columns_filter="true"
      :draggable_columns="true"
      @dragged_column="draggedColumn($event)"
      :fullscreen="true"
      @row-click="clickRow($event)"
      selection="multiple"
      file_name="sample"
      :selected="selected"
      row_key="name"
      @selected-val="getSelected($event)"
    >
    </q-grid>
    <q-dialog v-model="clickedRow.isOpen">
      <q-card>
        <q-card-section>
          <div class="text-h6">BİLGİ</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ clickedRow.data }}
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup>
import { ref } from "vue";

const selected = ref([]);
const clickedRow = ref({
  isOpen: false,
  data: null,
});

const clickRow = (evt) => {
  clickedRow.value.data = evt;
  clickedRow.value.isOpen = true;
};
const getSelected = (Selected) => {
  console.log(Selected);
};
const draggedColumn = (evt) => {
  console.log(evt);
};
const filteredData = (evt) => {
  console.log(evt);
};
const columns = ref([
  {
    name: "name",
    required: true,
    label: "Dessert (100g serving)",
    align: "left",
    field: "name",
    sortable: true,
  },
  {
    name: "calories",
    align: "center",
    label: "Calories",
    field: "calories",
    sortable: true,
  },
  { name: "fat", label: "Fat (g)", field: "fat", sortable: true },
  { name: "carbs", label: "Carbs (g)", field: "carbs" },
  { name: "protein", label: "Protein (g)", field: "protein" },
  { name: "sodium", label: "Sodium (mg)", field: "sodium" },
  {
    name: "calcium",
    label: "Calcium (%)",
    field: "calcium",
    sortable: true,
    sort: (a, b) => parseInt(a, 10) - parseInt(b, 10),
  },
  {
    name: "iron",
    label: "Iron (%)",
    field: "iron",
    sortable: true,
    sort: (a, b) => parseInt(a, 10) - parseInt(b, 10),
  },
  {
    name: "created_at",
    label: "Created At",
    field: "created_at",
    sortable: true,
    filter_type: "date",
    format: "DD/MM/YYYY",
  },
]);
const data = [
  {
    name: "Frozen Yogurt",
    calories: 159,
    fat: 6.0,
    carbs: 24,
    protein: 4.0,
    sodium: 87,
    calcium: "14%",
    iron: "1%",
    created_at: "13/4/2022",
  },
  {
    name: "Ice cream sandwich",
    calories: 237,
    fat: 9.0,
    carbs: 37,
    protein: 4.3,
    sodium: 129,
    calcium: "8%",
    iron: "1%",
    created_at: "23/4/2022",
  },
  {
    name: "Eclair",
    calories: 262,
    fat: 16.0,
    carbs: 23,
    protein: 6.0,
    sodium: 337,
    calcium: "6%",
    iron: "7%",
    created_at: "03/4/2022",
  },
  {
    name: "Cupcake",
    calories: 305,
    fat: 3.7,
    carbs: 67,
    protein: 4.3,
    sodium: 413,
    calcium: "3%",
    iron: "8%",
    created_at: "15/4/2022",
  },
  {
    name: "Gingerbread",
    calories: 356,
    fat: 16.0,
    carbs: 49,
    protein: 3.9,
    sodium: 327,
    calcium: "7%",
    iron: "16%",
    created_at: "05/4/2022",
  },
  {
    name: "Jelly bean",
    calories: 375,
    fat: 0.0,
    carbs: 94,
    protein: 0.0,
    sodium: 50,
    calcium: "0%",
    iron: "0%",
    created_at: "29/4/2022",
  },
  {
    name: "Lollipop",
    calories: 392,
    fat: 0.2,
    carbs: 98,
    protein: 0,
    sodium: 38,
    calcium: "0%",
    iron: "2%",
    created_at: "09/4/2022",
  },
  {
    name: "Honeycomb",
    calories: 408,
    fat: 3.2,
    carbs: 87,
    protein: 6.5,
    sodium: 562,
    calcium: "0%",
    iron: "45%",
    created_at: "19/4/2022",
  },
  {
    name: "Donut",
    calories: 452,
    fat: 25.0,
    carbs: 51,
    protein: 4.9,
    sodium: 326,
    calcium: "2%",
    iron: "22%",
    created_at: "09/4/2022",
  },
  {
    name: "KitKat",
    calories: 518,
    fat: 26.0,
    carbs: 65,
    protein: 7,
    sodium: 54,
    calcium: "12%",
    iron: "6%",
    created_at: "23/4/2022",
  },
];
</script>
