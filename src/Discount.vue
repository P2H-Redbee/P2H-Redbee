<template>
    <div class="discount">
        <h4>지금 결제하면 {{ 퍼센트 }}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: "Discount",
    props: {
        퍼센트: Number,
    },
};
</script>

<style></style>
