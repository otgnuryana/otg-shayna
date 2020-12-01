<template>
<div class="home">
    <HeaderSeries />
    <HeroSeries />
    <MouseSeries />
    <HeadsetsSeries />
    <KeyboardSeries />
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
import MouseSeries from "@/components/products/MouseSeries.vue";
import HeadsetsSeries from "@/components/products/HeadsetsSeries.vue";
import KeyboardSeries from "@/components/products/KeyboardSeries.vue";
import InstaSeries from "@/components/InstaSeries.vue";
import PartnerSeries from "@/components/PartnerSeries.vue";
import FooterSeries from "@/components/FooterSeries.vue";

export default {
    name: "Home",
    components: {
        HeaderSeries,
        HeroSeries,
        MouseSeries,
        HeadsetsSeries,
        KeyboardSeries,
        InstaSeries,
        PartnerSeries,
        FooterSeries,
    },
};
</script>
