<template>
<div class="product">
    <HeaderSeries />
    <!-- Breadcrumb Section Begin -->
    <div class="breadcrumb-section text-left">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                        <span>Detail</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="row">
                        <div class="col-lg-6">
                            <div class="product-pic-zoom">
                                <img class="product-big-img" :src="gambar_default" alt="" />
                            </div>
                            <div class="product-thumbs">
                                <carousel :dots="false" :nav="false" class="product-thumbs-track ps-slider">
                                    <div class="pt" @click="changeImage(thumbs[0])" :class="thumbs[0] == gambar_default ? 'active' : ''">
                                        <img src="img/view/view1.png" alt="" />
                                    </div>

                                    <div class="pt" @click="changeImage(thumbs[1])" :class="thumbs[1] == gambar_default ? 'active' : ''">
                                        <img src="img/view/view2.png" alt="" />
                                    </div>

                                    <div class="pt" @click="changeImage(thumbs[2])" :class="thumbs[2] == gambar_default ? 'active' : ''">
                                        <img src="img/view/view3.png" alt="" />
                                    </div>

                                    <div class="pt" @click="changeImage(thumbs[3])" :class="thumbs[3] == gambar_default ? 'active' : ''">
                                        <img src="img/view/view4.png" alt="" />
                                    </div>
                                </carousel>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="product-details text-left">
                                <div class="pd-title">
                                    <span>SteelSeries</span>
                                    <h3>AEROX 3</h3>
                                </div>
                                <div class="pd-desc">
                                    <p>
                                        Ultra lightweight (AKA super lightweight) mice are
                                        addictive. They allow gamers to flick them around at
                                        lightning speeds, which provides a huge edge in fast-paced
                                        games, and also removes a lot of strain. However,
                                        durability has been a major issue for ultra lightweight
                                        mice, from liquid damage, to dust, to static shocks, and
                                        more.
                                    </p>
                                    <p>
                                        The most noticible lightweight feature of Aerox is the
                                        perforated outer casing, with over 200 holes cut into the
                                        top and bottom of the mouse. This holey design shaves off
                                        about 18g of weight from the case alone, and allows the
                                        interior RGB to shine brighter than ever.
                                    </p>
                                    <h5>AquaBarrier™ Protection</h5>
                                    <br />
                                    <p>
                                        Engineered to safeguard the interior circuitry from
                                        virtually all types of environmental damage, Aerox is the
                                        first ever gaming mouse to receive an IP54 rating,
                                        providing water resistance and protection from dust, dirt,
                                        oil, fur, and more.
                                    </p>
                                    <h4>$69.99</h4>
                                </div>
                                <div class="quantity">
                                    <router-link to="/cart" class="primary-btn pd-cart">Add To Cart</router-link>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Product Shop Section End -->
    <RelatedSeries />
    <FooterSeries />
</div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderSeries from "@/components/HeaderSeries.vue";
import carousel from "vue-owl-carousel";
import RelatedSeries from "@/components/RelatedSeries.vue";
import FooterSeries from "@/components/FooterSeries.vue";

export default {
    name: "product",
    components: {
        HeaderSeries,
        carousel,
        RelatedSeries,
        FooterSeries,
    },
    data() {
        return {
            gambar_default: "img/view/view1.png",
            thumbs: [
                "img/view/view1.png",
                "img/view/view2.png",
                "img/view/view3.png",
                "img/view/view4.png",
            ],
        };
    },
    methods: {
        changeImage(urlImage) {
            this.gambar_default = urlImage;
        },
    },
};
</script>

<style scoped>
.product-thumbs .pt {
    margin-right: 14px;
}
</style>
