<template>
    <div class="dialog fixed top-10 right-0 left-0 z-50 m-auto flex justify-center rounded-lg">
        <div class="relative">
            <!--content -->
            <div v-if="itemModal" id="popup-modal" tabindex="-1" class="relative bg-gray-200 rounded-lg bg-gray-200 w-[950px]" >
                <!--header -->
                <button @click="closeDialog" type="button" class="absolute top-3 end-2.5 text-dark text-sm w-8 h-8 ms-auto inline-flex justify-center items-center" data-modal-hide="popup-modal" >
                    <svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"/>
                    </svg>
                    <span class="sr-only">Close modal</span>
                </button>
                <!--body-->
                <div class="lg:h-[500px] md:h-[400px] h-[450px] overflow-y-auto overflow-x-hidden lg:mb-5 md:mb-4 mb-5">    
                    <div class="mt-5">
                        <img :src="itemModal.flags.png" alt="flag" class="w-30 h-24 m-auto mb-2"/>
                        <strong class="text-xl uppercase text-center">{{itemModal.name.official}}</strong>
                    </div>
                    <div class="bg-gray-100 lg:flex md:flex mx-10 rounded-lg my-3">           
                        <div class="w-full py-3 h-auto mx-8 my-5">
                            <div class="flex mb-1">
                                <div class="flex text-start lg:w-6/12 md:w-[60%] whitespace-normal">
                                    <strong class="mr-3">International direct dialing :</strong>          
                                    {{itemModal.idd.root}}<span v-for="(suff,i) in itemModal.idd.suffixes" :key="i" class="ml-2">( {{suff}} )</span>
                                </div>
                                <div class="flex text-start lg:w-6/12">
                                    <strong class="mr-3">Subregion :</strong>             
                                    {{itemModal.subregion}}
                                </div>
                            </div>
                            <div class="flex mb-1">
                                <div class="flex text-start lg:w-6/12">
                                    <strong class="mr-3">CAA2 & CAA3 :</strong>             
                                    {{itemModal.cca2}} / {{itemModal.cca3}}
                                </div>
                                <div class="flex text-start lg:w-6/12">
                                    <strong class="mr-3">CIOC & CCN3 :</strong>              
                                    {{itemModal.cioc}} / {{itemModal.ccn3}}
                                </div>
                            </div>
                            <div class="lg:flex md:flex gap-3 lg:mb-3 md:mb-2">
                                <div class="flex text-start lg:w-6/12 md:w-[60%] whitespace-normal">
                                    <strong class="mr-3">Top-level domain :</strong>    
                                    <div v-for="(capital,i) in itemModal.capital" :key="i">
                                        {{capital}}
                                    </div>
                                </div>
                                <div class="flex text-start lg:w-6/12">
                                    <strong class="mr-3">Status of Country :</strong>    
                                    {{itemModal.status}}
                                </div>
                            </div>
                            <div class="lg:flex md:flex gap-3 lg:mb-3 md:mb-2">
                                <div class="flex text-start lg:w-6/12 md:w-[60%] whitespace-normal">
                                    <strong class="mr-3">Capital of Country :</strong>           
                                    <div v-for="(capital,i) in itemModal.capital" :key="i">
                                        {{capital}}
                                    </div>
                                </div>
                                <div class="flex text-start lg:w-6/12">
                                    <strong class="mr-3">Population :</strong>             
                                    {{itemModal.population}}
                                </div>
                            </div>
                            <div class="flex text-start lg:w-6/8 mb-4 md:w-[96%]">
                                <strong class="mr-3 w-52">AltSpellings Country :</strong>             
                                <div v-for="(altspelling,i) in itemModal.altSpellings" :key="i">
                                    {{altspelling}},  
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div v-if="itemModal" class="fixed top-0 left-0 right-0 bottom-0 bg-black bg-opacity-10 z-20"></div>
</template>

<script>
export default {
    props: {
        itemModal: Array,
    },
    methods: {
        closeDialog() {
            this.$emit("close");
        },
    },
};
</script>