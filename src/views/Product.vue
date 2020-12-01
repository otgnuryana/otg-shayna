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
                                <img class="product-big-img" :src="'https://backend.otg-web.site/storage/'+gambar_default" alt="" />
                            </div>
                            <div class="product-thumbs" v-if="productDetails.galleries.length > 0">
                                <carousel :dots="false" :nav="false" class="product-thumbs-track ps-slider">
                                    <div v-for="ss in productDetails.galleries" :key="ss.id" class="pt" @click="changeImage(ss.photo)" :class="ss.photo[0] == gambar_default ? 'active' : ''">
                                        <img :src="'https://backend.otg-web.site/storage/'+ss.photo" alt="" />
                                    </div>
                                </carousel>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="product-details text-left">
                                <div class="pd-title">
                                    <span>{{ productDetails.type }}</span>
                                    <h3>{{ productDetails.name }}</h3>
                                </div>
                                <div class="pd-desc">
                                    <p>{{ productDetails.description}}</p>
                                    <h4>${{ productDetails.price }}.99</h4>
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
import axios from "axios";

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
            gambar_default: '',
            thumbs: [
                "img/view/view1.png",
                "img/view/view2.png",
                "img/view/view3.png",
                "img/view/view4.png",
            ],
            productDetails:[]
        };
    },
    methods: {
        changeImage(urlImage) {
            this.gambar_default = urlImage;
        },
        setDataPicture(data){
            // replace object productDetails dengan data dari API
            this.productDetails = data;
            // replace value gambar default dengan data dari API (galleries)
            this.gambar_default = data.galleries[0].photo
        }
    },
    mounted() {
        axios
            .get("https://backend.otg-web.site/api/products", {
                params: {
                    id: this.$route.params.id
                }   
            })
            .then(res => (this.setDataPicture(res.data.data)))
            // eslint-disable-next-line no-console
            .catch(err => console.log(err));
    },
};
</script>

<style scoped>
.product-thumbs .pt {
    margin-right: 14px;
}
</style>
