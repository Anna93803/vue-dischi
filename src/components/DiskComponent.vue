<template>
    <div class="bg-card">
        <div class="card">
            <img :src="imgUrl" :alt="titleImg">
            <h4>{{ titleImg }}</h4>
            <p>{{ author }}</p>
            <p>{{ year }}</p>
        </div>
    </div>
</template>

<script>

export default {
    name: 'DiskComponent',
    props: {
        imgUrl: String,
        titleImg: String,
        author: String,
        year: String,
    },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

.bg-card {
    background-color:  $ColorSecondary;
    height: 100%;
    padding: 1.5625rem;

    .card {
        text-align: center;

        img {
            width: 100%;
            padding-bottom: .9375rem;
        }

        h4 {
            color: $ColorTextLight;
            text-transform: uppercase;
            font-size: 1.0625rem;
            padding-bottom: .9375rem;
        }

        p {
            color: $ColorText;
        }
    }
}

</style>