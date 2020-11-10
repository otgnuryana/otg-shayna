<template>
<div class="home">
    <HeaderShayna />
    <HeroShayna />
    <BannerShayna />
    <InstaShayna />
</div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from "@/components/HeaderShayna.vue";
import HeroShayna from "@/components/HeroShayna.vue";
import BannerShayna from "@/components/BannerShayna.vue";
import InstaShayna from "@/components/InstaShayna.vue";

export default {
    name: "Home",
    components: {
        HeaderShayna,
        HeroShayna,
        BannerShayna,
        InstaShayna,
    },
};
</script>
