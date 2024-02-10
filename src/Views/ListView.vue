<template>
    <div class="list">
        <ListComponent :items = "items"/>
    </div>
</template>

<script>
import axios from "axios";
import ListComponent from '@/components/ListComponent.vue';
export default {
    components:{
        ListComponent
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