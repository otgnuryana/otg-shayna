<template>
<div class="shopping">
    <HeaderSeries />

    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section">
        <div class="container">
            <div class="row">
                <div class="col-lg-12 text-left">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                        <span>Shopping Cart</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Shopping Cart Section Begin -->
    <section class="shopping-cart spad">
        <div class="container">
            <div class="row">
                <div class="col-lg-8">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="cart-table">
                                <table>
                                    <thead>
                                        <tr>
                                            <th>Image</th>
                                            <th class="p-name text-center">Product Name</th>
                                            <th>Price</th>
                                            <th>Action</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr v-for="keranjang in keranjangUser" :key="keranjang.id">
                                            <td class="cart-pic first-row">
                                                <img :src="'https://backend.otg-web.site/storage/' + keranjang.photo" />
                                            </td>
                                            <td class="cart-title first-row text-center">
                                                <h5>{{ keranjang.name }}</h5>
                                            </td>
                                            <td class="p-price first-row">${{ keranjang.price }}.00</td>
                                            <td class="delete-item" @click="hapusItem(keranjang.id)">
                                                <a href="#"><i class="material-icons"> close </i></a>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                        <div class="col-lg-8 text-left">
                            <h4 class="mb-4">Informasi Pembeli:</h4>
                            <div class="user-checkout">
                                <form>
                                    <div class="form-group">
                                        <label for="namaLengkap">Nama lengkap</label>
                                        <input type="text" class="form-control" id="namaLengkap" aria-describedby="namaHelp" placeholder="Masukan Nama" 
                                        v-model="customerInfo.nama"
                                        />
                                    </div>
                                    <div class="form-group">
                                        <label for="namaLengkap">Email Address</label>
                                        <input type="email" class="form-control" id="emailAddress" aria-describedby="emailHelp" placeholder="Masukan Email" 
                                        v-model="customerInfo.email"/>
                                    </div>
                                    <div class="form-group">
                                        <label for="namaLengkap">No. HP</label>
                                        <input type="text" class="form-control" id="noHP" aria-describedby="noHPHelp" placeholder="Masukan No. HP" 
                                        v-model="customerInfo.number"/>
                                    </div>
                                    <div class="form-group">
                                        <label for="alamatLengkap">Alamat Lengkap</label>
                                        <textarea class="form-control" id="alamatLengkap" rows="3" v-model="customerInfo.address"></textarea>
                                    </div>
                                </form>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="proceed-checkout text-left">
                                <ul>
                                    <li class="subtotal">
                                        ID Transaction <span>#SH12000</span>
                                    </li>
                                    <li class="subtotal mt-3">Subtotal <span>${{ totalHarga }}.00</span></li>
                                    <li class="subtotal mt-3">Pajak <span>10% | ${{ totalHarga * 10 / 100 }}</span></li>
                                    <li class="subtotal mt-3">
                                        Total Biaya <span>${{ totalBiaya }}</span>
                                    </li>
                                    <li class="subtotal mt-3">
                                        Bank Transfer <span>Mandiri</span>
                                    </li>
                                    <li class="subtotal mt-3">
                                        No. Rekening <span>2208 1996 1403</span>
                                    </li>
                                    <li class="subtotal mt-3">
                                        Nama Penerima <span>Series</span>
                                    </li>
                                </ul>
                                <!-- <router-link to="/success" class="proceed-btn">I ALREADY PAID</router-link> -->
                               <a @click="checkout()" href="/#/" class="proceed-btn">I ALREADY PAID</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Shopping Cart Section End -->
</div>
</template>

<script>
import HeaderSeries from "@/components/HeaderSeries.vue";
import axios from "axios";

export default {
    name: "ShoppingCart",
    components: {
        HeaderSeries,
    },
    data() {
        return {
            keranjangUser: [],
            customerInfo: {
                nama: '',
                email: '',
                number: '',
                address: '',
            }
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
        },
        // fungsi mengirim data ke API
        checkout(){
            let productIds = this.keranjangUser.map(function(product){
                return product.id;
            });
            let checkoutData = {
                'name': this.customerInfo.nama,
                'email': this.customerInfo.email,
                'number': this.customerInfo.number,
                'address': this.customerInfo.address,
                'transaction_total': parseInt(this.totalBiaya),
                'transaction_status': "PENDING",
                'transaction_details': productIds
            }
            axios
                .post(
                    "https://backend.otg-web.site/api/checkout",
                    checkoutData
                )
                .then(() => this.$router.push("success"))
                // eslint-disable-nextline no console
                .catch(err => console.log(err)); 
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
            } , 0 );
        },
        totalBiaya(){
            return this.totalHarga * 10 / 100 + this.totalHarga
        }
    }
};
</script>

<style scoped>
</style>
