<template>
<div>
    <!-- Hero Section Begin -->
    <section class="hero-section">
        <carousel class="hero-items" :autoplay="true" :loop="true" :items="1" :nav="false">
            <div class="single-hero-items set-bg" style="background-image: url(img/bg1.jpg)">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-5">
                            <span>Gaming Gear</span>
                            <h1>Black friday</h1>
                            <p>
                                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed
                                do eiusmod tempor incididunt ut labore et dolore
                            </p>
                            <a href="#" class="primary-btn">Shop Now</a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="single-hero-items set-bg" style="background-image: url(img/bg2.jpg)">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-5">
                            <span>Elegant Style</span>
                            <h1>Black friday</h1>
                            <p class="text-white">
                                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed
                                do eiusmod tempor incididunt ut labore et dolore
                            </p>
                            <a href="#" class="primary-btn">Shop Now</a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="single-hero-items set-bg" style="background-image: url(img/bg3.jpg)">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-5">
                            <span>Gaming Everytime</span>
                            <h1>Black friday</h1>
                            <p class="text-white">
                                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed
                                do eiusmod tempor incididunt ut labore et dolore
                            </p>
                            <a href="#" class="primary-btn">Shop Now</a>
                        </div>
                    </div>
                </div>
            </div>
        </carousel>
    </section>
    <!-- Hero Section End -->
</div>
</template>

<script>
import carousel from "vue-owl-carousel";

export default {
    name: "HeroShayna",
    components: {
        carousel,
    },
};
</script>

<style scoped>
</style>
