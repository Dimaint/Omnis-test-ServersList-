<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row class="mt-4">
          <v-col>
            <ServerList :list="serversList" @openServer="openServer" />
          </v-col>
          <v-col>
            <ServerForm :server="selected" @saveForm="saveForm"/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
const serversList = ref([
  { customer_id: "user1", server_name: "server7", server_type: "vds" },
  { customer_id: "user5", server_name: "server2", server_type: "dedicated" },
  { customer_id: "user3", server_name: "server4", server_type: "hosting" },
]);
const selected = ref();
const selectedIndex = ref();
const openServer = (item, index) => {
  selected.value = item;
  selectedIndex.value = index;
};
const saveForm = (formData) => {
  serversList.value[selectedIndex.value].server_name = formData.server_name
  serversList.value[selectedIndex.value].server_type = formData.server_type 
}
</script>
