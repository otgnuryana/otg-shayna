<template>
<div>
    <!-- Hero Section Begin -->
    <section class="hero-section">
        <carousel class="hero-items" :autoplay="true" :loop="true" :items="1" :nav="false">
            <div class="single-hero-items set-bg" style="background-image: url(img/bg1.jpg)">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-5">
                            <span>Gaming Mice</span>
                            <h1>Aerox Series</h1>
                            <p class="text-white">
                                SteelSeries has designed a wired and wireless gaming mouse for
                                every gamer and they’re built for gaming precision with
                                optical tracking sensors and hyper durable materials.
                            </p>
                            <a href="#mouse" class="primary-btn">Shop Now</a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="single-hero-items set-bg" style="background-image: url(img/bg2.jpg)">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-5">
                            <span>Mechanical Keyboard</span>
                            <h1>Apex Pro</h1>
                            <p class="text-white">
                                The Apex Pro is the biggest leap in mechanical keyboards since
                                the invention of the mechanical switch over 35 years ago. Each
                                key can be adjusted to meet your preferred sensitivity level,
                                whether it’s for gaming, work, or anything else.
                            </p>
                            <a href="#keyboard" class="primary-btn">Shop Now</a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="single-hero-items set-bg" style="background-image: url(img/bg7.jpg)">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-5">
                            <span>Gaming Headsets</span>
                            <h1>Arctis Series</h1>
                            <p class="text-white">
                                Enjoy the award-winning sound, comfortable design, and durable
                                quality of the best Arctis multi-platform gaming headsets in
                                both wired and wireless, compatible with PC, Mac, Xbox One,
                                Xbox Series X, PlayStation 4, Nintendo Switch, mobile, and
                                more.
                            </p>
                            <a href="#headset" class="primary-btn">Shop Now</a>
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
    name: "HeroSeries",
    components: {
        carousel,
    },
};
</script>

<style scoped>
.primary-btn :hover{
    background-color: rgb(255, 198, 93);
}
</style>
