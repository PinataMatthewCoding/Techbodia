<template>
    <div class="lg:mx-20 md:mx-10 mx-5">
        <!-- content table  -->
        <div class="overflow-x-auto w-full">
            <table class="table-auto border-collapse border-1 border-gray-500 sm:overflow-x-auto w-full text-center">
                <thead>
                    <tr class="text-xl">
                        <th class="border border-gray-400 py-5">N.o</th>
                        <th class="border border-gray-400 py-5">Code</th>
                        <th class="border border-gray-400 py-5">Flags</th>
                        <th class="border border-gray-400 py-5">Country Name</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in filteredItems" :key="index" class="hover:bg-gray-100 lg:text-lg md:text-lg text-xs">
                        <td class="border border-gray-400 py-2">{{ index + 1 }}</td>
                        <td class="border border-gray-400 py-2">{{ item.idd.root }}</td>
                        <td class="flex justify-center border border-gray-400 py-2">
                        <img :src="item.flags.png" alt="flags" class="w-20 h-10">
                        </td>
                        <td @click="openDialog(item)" class="border border-gray-400 py-2 cursor-pointer">{{ item.name.official }}</td>
                        <!-- modal -->
                        <ModalComponent v-if="dialogView" :itemModal="selectedItem" @close="closeDialog" />
                    </tr>
                </tbody>
            </table>
        </div>
        <!-- pagination  -->
        <div class="flex justify-end my-4">
            <button :disabled="currentPage === 1" @click="previousPage" class="px-4 py-2 mx-1 bg-pink-600 text-white rounded">
                Previous
            </button>
            <button :disabled="currentPage === totalPages" @click="nextPage" class="px-4 py-2 mx-1 bg-pink-600 text-white rounded">
                Next
            </button>
        </div>
    </div>
</template>

<script>
import Fuse from 'fuse.js';
import ModalComponent from './ModalComponent.vue';

export default {
    props: {
        items: Array,
    },
    components: {
        ModalComponent,
    },
    data() {
        return {
            pageRow: 25,
            currentPage: 1,
            dialogView: false,
            selectedItem: null,
            searchQuery: '',
        };
    },
    methods: {
        // pagination
        previousPage() {
            if (this.currentPage > 1) {
                this.currentPage--;
            }
        },
        nextPage() {
            if (this.currentPage < this.totalPages) {
                this.currentPage++;
            }
        },
        // Modal
        openDialog(item) {
            this.selectedItem = item;
            this.dialogView = true;
        },
        closeDialog() {
            this.dialogView = false;
        },
    },
    computed: {
        // Order by ASC
        sortedItems() {
            const sortedArray = this.items.slice();
            return sortedArray.sort((a, b) => {
                const nameA = a.name.official.toUpperCase();
                const nameB = b.name.official.toUpperCase();
                if (nameA < nameB) {
                    return -1;
                }
                if (nameA > nameB) {
                    return 1;
                }
                return 0;
            });
        },
        // Pagination
        totalPages() {
            return Math.ceil(this.sortedItems.length / this.pageRow);
        },
        displayedItems() {
            const startIndex = (this.currentPage - 1) * this.pageRow;
            const endIndex = startIndex + this.pageRow;
            return this.sortedItems.slice(startIndex, endIndex);
        },
        // fuzzy
        filteredItems() {
            if (this.searchQuery) {
                const options = {
                    keys: ['item.name.official'],
                    threshold: 0.4,
                };
                const fuse = new Fuse(this.displayedItems, options);
                return fuse.search(this.searchQuery).map(result => result.item);
            }
            return this.displayedItems;
        },
    },
    watch: {
        searchQuery() {
            this.currentPage = 1;
        },
    },
};
</script>