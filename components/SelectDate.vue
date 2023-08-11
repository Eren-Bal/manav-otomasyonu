<template>
  <v-menu
    ref="menu"
    v-model="menu"
    :close-on-content-click="false"
    transition="scale-transition"
    offset-y
    min-width="auto"
  >
    <template v-slot:activator="{ on, attrs }">
      <v-text-field
        v-model="date"
        :label="label"
        readonly
        v-bind="attrs"
        v-on="on"
        dense
        hide-details
        outlined
      ></v-text-field>
    </template>
    <v-date-picker
      v-model="date"
      :active-picker.sync="activePicker"
      max="2025-01-01"
      min="2022-01-01"
      @change="save"
    ></v-date-picker>
  </v-menu>
</template>
<script>
export default {
  props: ["label"],
  data: () => ({
    activePicker: null,
    date: null,
    menu: false,
  }),
  watch: {
    menu(val) {
      val && setTimeout(() => (this.activePicker = "YEAR"));
    },
  },
  methods: {
    save(date) {
      this.$refs.menu.save(date);
      this.$emit("date", date);
    },
  },
};
</script>
