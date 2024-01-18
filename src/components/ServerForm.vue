<template lang="">
  <v-sheet width="400" class="mx-auto">
    <v-text-field
      v-model="formData.server_name"
      :counter="100"
      label="Name"
    ></v-text-field>

    <v-select
      v-model="formData.server_type"
      :items="typeList"
      label="Type"
      required
    ></v-select>

    <v-btn color="green" class="mt-4" block @click="save"> Сохранить </v-btn>
  </v-sheet>
</template>
<script setup>
import { ref, watch } from "vue";
const props = defineProps(["server"]);

const formData = ref({
  server_name: "",
  server_type: "",
  customer_id: "",
});

const typeList = ref(["vds", "hosting", "dedicated"]);

const save = () => {
  emit("saveForm", formData.value);
};
const emit = defineEmits(["saveForm"]);
watch(props, () => {
  formData.value.server_name = props.server.server_name;
  formData.value.server_type = props.server.server_type;
});
</script>
<style lang=""></style>
