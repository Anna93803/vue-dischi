<template>
    <div class="bg-main">
        <div class="container">
            <div class="select">
                <select name="filtro" id="filtro" v-model="selectValue" >
                    <option value="">Seleziona il genere</option>
                    <option v-for="(generi, i) in selectedGenre" :key="i" :value="generi"> {{ generi }}</option>
                </select>
                <select name="filtro" id="filtro" v-model="selectValue" >
                    <option value="">Seleziona Author</option>
                    <option v-for="(author, i) in selectedAuthor" :key="i" :value="author"> {{ author }}</option>
                </select>
            </div>
            <div class="row">
                <div class="col" v-for="(disk, i) in filterGenre" :key="i">
                    <DiskComponent  
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
            genreList: [],
            auhtorList: [],
            selectValue: '',
        };
    },
    methods: {
        diskList() {
            axios.get(this.apiUrl).then((resp) => {
                this.arrayList = resp.data.response;
            })
            .catch(() => {
                alert("Loperazione non è andata a buon fine.")
            })
        },
    },
    mounted() {
        this.diskList();
    },
    computed: {
        selectedGenre() {

            this.arrayList.forEach((element) => {
                if (!this.genreList.includes(element.genre)) {
                    this.genreList.push(element.genre)
                }
            })

            return this.genreList
        },
        filterGenre() {
            if(!this.selectValue) {
                return this.arrayList
            }

            return this.arrayList.filter((album) => {
                return album.genre === this.selectValue;
        
            });
        },
        selectedAuthor() {
            this.arrayList.forEach((element) => {
                if(!this.auhtorList.includes(element.author)) {
                    this.auhtorList.push(element.author)
                }
            })

            return this.auhtorList
        },   
    },
}

</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

.bg-main {
    height: 100%;
    overflow: auto;

    .container {
        max-width: 1200px;
        margin: 0 auto;

        .select {
            background-color: $ColorSecondary;
            padding: 20px;
            margin-top: 30px;

            #filtro {
                margin-right: 36px;
            }
        }
        .row {
            padding: 5.125rem 0;
            display: flex;
            flex-wrap: wrap;
            gap: .9375rem;
            .col {
                width: calc(20% - .9375rem);
            }
        }
    }
}

</style>