<template>
    <transition name="fade">
        <Modal
            :원룸들="원룸들"
            :누른번호="누른번호"
            :열림="열림"
            @closeModal="열림 = 'ㄴㄴ'"
        />
    </transition>
    <div class="menu">
        <a v-for="a in 메뉴들" :key="a" href="#"> {{ a }}</a>
    </div>
    <Discount :퍼센트="퍼센트" />

    <button @click="priceSort">가격 순 정렬</button>
    <button @click="priceSortReverse">가격 역순 정렬</button>
    <button @click="charSort">가나다 순 정렬</button>
    <button @click="filterSort">50만원 이하 상품</button>
    <button @click="sortBack">되돌리기</button>

    <Card
        @openModal="
            열림 = 'ㅇㅇ';
            누른번호 = $event;
        "
        :원룸="원룸들[i]"
        v-for="(원룸, i) in 원룸들"
        :key="i"
    />
</template>

<script>
import data from "./assets/data.js";
import Card from "./Card.vue";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";

export default {
    name: "App",
    methods: {
        priceSort() {
            this.원룸들.sort(function (a, b) {
                return a.price - b.price;
            });
        },
        priceSortReverse() {
            this.원룸들.sort(function (a, b) {
                return b.price - a.price;
            });
        },
        charSort() {
            this.원룸들.sort(function (a, b) {
                return a.title[0] - b.title[0];
            });
        },
        filterSort() {
            this.원룸들 = this.원룸들.filter((a) => {
                return a.price <= 500000;
            });
        },
        sortBack() {
            this.원룸들 = [...this.원룸들오리지널];
        },
        countDown() {
            setInterval(() => {
                this.퍼센트 -= 1;
            }, 1000);
        },
    },
    data() {
        return {
            퍼센트: 30,
            원룸들오리지널: [...data],
            누른번호: 0,
            원룸들: data,
            열림: "ㄴㄴ",
            products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
            prices: [20, 5, 10],
            신고수: [0, 0, 0, 0, 0, 0],
            메뉴들: ["Home", "Shop", "About"],
        };
    },
    mounted() {
        this.countDown();
    },

    components: { Modal, Card, Discount },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    filter: blur(4px);
}
.fade-enter-active,
.fade-leave-active {
    transition: all 1s;
}
.fade-enter-to,
.fade-leave-from {
    opacity: 1;
    filter: blur(0px);
}
.discount {
    background-color: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
img {
    width: 100%;
}
.home {
    margin-top: 30px;
}
.menu {
    background-color: blueviolet;
    padding: 20px;
}
.menu a {
    color: #fff;
    margin: 15px;
    font-size: 17pt;
    text-decoration: none;
}

div {
    box-sizing: border-box;
}
.black-bg {
    background-color: #0000006b;
    position: fixed;
    left: 0px;
    top: 0px;
    width: 100%;
    height: 100%;
    padding: 20px;
}

.white-bg {
    width: 70%;
    margin: 0 auto;
    background-color: #ffffff;
    border-radius: 10px;
    padding: 20px;
}
</style>
