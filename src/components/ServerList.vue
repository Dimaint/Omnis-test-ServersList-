<template>
  <v-card class="mx-auto" max-width="300">
    <v-list lines="one">
      <v-list-item
        v-for="(item, index) in list"
        :key="index"
        :title="item.server_name"
        :subtitle="item.server_type"
        @click-once="select(item, index)"
      ></v-list-item>
    </v-list>
  </v-card>
</template>

<script setup>
const props = defineProps(["list"]);

const select = (item, index) => {
  console.log(toRaw(item));
  emit("openServer", item, index);
};
const emit = defineEmits(["openServer"]);
</script>
