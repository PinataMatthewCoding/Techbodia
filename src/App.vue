<template>
  <div class="header"><HeaderComponent/></div>
  <div class="list-items"><NavbarComponent /></div>
  <div class="text-content text-center text-2xl font-bold">
    Countries Catalog Implementation
  </div>
  <div class="list-items mt-5"><ListView /></div>
  <div class="list-items"><FooterComponent /></div>
</template>

<script>
import ListView from "./Views/ListView.vue";
import HeaderComponent from "@/components/header/HeaderComponent.vue";
import NavbarComponent from './components/header/NavbarComponent.vue';
import FooterComponent from './components/footer/FooterComponent.vue';

export default {
  components:{
    ListView,
    HeaderComponent,
    NavbarComponent,
    FooterComponent
  },
};
</script>