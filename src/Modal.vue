<template>
    <div class="black-bg" v-if="열림 == 'ㅇㅇ'">
        <div class="white-bg">
            <h2>{{ 원룸들[누른번호].title }}</h2>
            <p>{{ 원룸들[누른번호].content }}</p>
            <input v-model.number="month" />
            <p>
                {{ month }}개월 선택함 : {{ 원룸들[누른번호].price * month }}원
            </p>
            <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Modal",
    data() {
        return {
            month: 1,
        };
    },
    beforeUpdate() {
        if (this.month < 3) {
            alert("3개월치 부터 하세요");
        }
    },
    watch: {
        month(a, b) {
            if (a >= 13) {
                alert("13이상 입력 ㄴ");
                this.month = b;
            }
            if (isNaN(a) == true) {
                this.month = 1;
                alert("글씨입력 ㄴ");
            }
            console.log(typeof i);
        },
    },
    props: {
        원룸들: Array,
        열림: String,
        누른번호: Number,
    },
};
</script>

<style>
img {
    width: 100%;
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
