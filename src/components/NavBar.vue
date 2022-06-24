<template>
    <div class="bg-navbar">
        <div class="logo">
            <img src="../assets/img/logo-small.svg" alt="logo-spotify">
        </div>
    </div>
</template>


<script>

export default {
    name: 'NavBar',
}

</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

.bg-navbar {
    background-color:  $ColorSecondary;
    padding: .5rem;

    .logo {
        width: 45px;

        img {
            width: 100%;
        }
    }
}
</style>
