<template>
<div>
    <!-- Header Section Begin -->
    <header class="header-section">
        <div class="header-top">
            <div class="container">
                <div class="ht-left">
                    <div class="mail-service">
                        <i class="fa fa-envelope"></i> hello@x-series.com
                    </div>
                    <div class="phone-service">
                        <i class="fa fa-instagram"></i> x_series
                    </div>
                </div>
            </div>
        </div>
        <div class="container">
            <div class="inner-header">
                <div class="row">
                    <div class="col-lg-2 col-md-2">
                        <div class="logo">
                            <router-link to="/">
                                <img src="img/logonew.png" alt="" />
                            </router-link>
                        </div>
                    </div>
                    <div class="col-lg-7 col-md-7"></div>
                    <div class="col-lg-3 text-right col-md-3">
                        <ul class="nav-right">
                            <li class="cart-icon">
                                Shopping Cart &nbsp;
                                <a href="#">
                                    <i class="icon_bag_alt"></i>
                                    <span>{{ keranjangUser.length }}</span>
                                </a>
                                <div class="cart-hover">
                                    <div class="select-items">
                                        <table>
                                            <tbody v-if="keranjangUser.length > 0">
                                                <tr v-for="keranjang in keranjangUser" :key="keranjang.id">
                                                    <td class="si-pic">
                                                        <img :src="'https://backend.otg-web.site/storage/' + keranjang.photo" alt="" />
                                                    </td>
                                                    <td class="si-text">
                                                        <div class="product-selected">
                                                            <p>${{ keranjang.price }}.00 x1</p>
                                                            <h6>{{ keranjang.name }}</h6>
                                                        </div>
                                                    </td>
                                                    <td 
                                                    @click="hapusItem(keranjang.id)"
                                                    class="si-close">
                                                        <i class="ti-close"></i>
                                                    </td>
                                                </tr>                                       
                                            </tbody>
                                            <tbody v-else class="text-center">
                                                <p>Cart Kosong</p>
                                            </tbody>
                                        </table>
                                    </div>
                                    <div class="select-total">
                                        <span>total:</span>
                                        <h5>${{ totalHarga }}.00</h5>
                                    </div>
                                    <div class="select-button">
                                        <a href="/#/cart/" class="primary-btn view-card">VIEW CARD</a>
                                        <a href="/#/cart/" class="primary-btn checkout-btn">CHECK OUT</a>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </header>
    <!-- Header End -->
</div>
</template>

<script>
export default {
    name: "HeaderSeries",
    data() {
        return {
            keranjangUser: []
        }
    },
    methods: {
        hapusItem(idx) {
            // cari tahu id dari item yang akan di hapus
            let keranjangUserStorage = JSON.parse(localStorage.getItem("keranjangUser"));
            let itemKeranjangUserStorage = keranjangUserStorage.map(itemKeranjangUserStorage => itemKeranjangUserStorage.id);

            // cocokan idx dengan id yang ada di local storage
            let index = itemKeranjangUserStorage.findIndex(id => id == idx);
            this.keranjangUser.splice(index, 1);

            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem("keranjangUser", parsed);
        }
    },
    mounted() {
        if (localStorage.getItem("keranjangUser")) {
                try {
                    this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
                } catch(e) {
                    localStorage.removeItem("keranjangUser");
                }
            }
    },
    computed: {
        totalHarga(){
            return this.keranjangUser.reduce(function(items, data){
                return items + data.price;
            } ,0);
        }
    }
};
</script>

<style scoped>
</style>
