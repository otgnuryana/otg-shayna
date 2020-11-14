<template>
<div class="home">
    <HeaderSeries />
    <HeroSeries />
    <BannerSeries />
    <InstaSeries />
    <PartnerSeries />
    <FooterSeries />
</div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderSeries from "@/components/HeaderSeries.vue";
import HeroSeries from "@/components/HeroSeries.vue";
import BannerSeries from "@/components/BannerSeries.vue";
import InstaSeries from "@/components/InstaSeries.vue";
import PartnerSeries from "@/components/PartnerSeries.vue";
import FooterSeries from "@/components/FooterSeries.vue";

export default {
    name: "Home",
    components: {
        HeaderSeries,
        HeroSeries,
        BannerSeries,
        InstaSeries,
        PartnerSeries,
        FooterSeries,
    },
};
</script>
