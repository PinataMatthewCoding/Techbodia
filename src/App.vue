<template>
  <div class="header"><HeaderComponent/></div>
  <div class="list-items mt-5"><ListView /></div>
</template>

<script>
import ListView from "./Views/ListView.vue";
import HeaderComponent from "@/components/header/HeaderComponent.vue";

export default {
  components:{
    ListView,
    HeaderComponent,
  },
};
</script>