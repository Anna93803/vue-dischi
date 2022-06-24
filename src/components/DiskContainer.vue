<template>
    <div class="bg-main">
        <div class="container">
            <div class="row">
                <div class="col">
                    <DiskComponent  v-for="(disk, i) in arrayList" :key="i"
                    :imgUrl="disk.poster" 
                    :titleImg="disk.title"
                    :author="disk.author"
                    :year="disk.year">
                    </DiskComponent>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import DiskComponent from "./DiskComponent.vue";

export default {
    name: "DiskContainer",
    components: {
        DiskComponent,
    },
    data() {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            arrayList: [],
        };
    },
    methods: {
        diskList() {
            axios.get(this.apiUrl).then((resp) => {
                this.arrayList = resp.data.response;
            });
        },
    },
    mounted() {
        this.diskList();
    },
}

</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

.bg-main {
    background-color: $ColorPrimary;

    .container {
        max-width: 1200px;
        margin: 0 auto;

        .row {
            padding: 5.125rem 0;
            .col {
                display: flex;
                justify-content: center;
                flex-wrap: wrap;
                gap: 2.5rem;
            }
        }
    }
}

</style>