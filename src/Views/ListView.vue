<template>
    <div class="list-items"><NavbarComponent /></div>
    <div class="list"><ListComponent :items = "items"/></div>
    <div class="list-items"><FooterComponent /></div>
</template>

<script>
import axios from "axios";
import ListComponent from '@/components/ListComponent.vue';
import NavbarComponent from '@/components/header/NavbarComponent.vue';
import FooterComponent from '@/components/footer/FooterComponent.vue';
export default {
    components:{
        ListComponent,
        NavbarComponent,
        FooterComponent
    },
    data() {
        return {
            items: [],
        };
    },
    methods: {
        fetchData() {
            axios
                .get("https://restcountries.com/v3.1/all")
                .then((response) => {
                this.items = response.data;
                })
                .catch((error) => {
                console.error("Error fetching data:", error);
                });
            },
    },
    mounted() {
        this.fetchData();
    },
};
</script>