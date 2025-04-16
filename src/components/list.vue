<template>
    <div>
        <div v-for="(item, index) in list" class="item" :class="activeIndex == index ? 'sha' : ''"
            @mouseenter="enter(index)">
            <div class="item-left">
                <img :src="item.url" alt="">
            </div>
            <div class="item-right">
                <p>{{ item.title }}</p>
                <p>{{ item.desc }}</p>
            </div>
        </div>
    </div>

</template>

<script setup>
import { ref } from 'vue'
const prop = defineProps({
    list: {
        type: Array,
        default: []
    }
})
const activeIndex = ref(undefined)
function enter(index) {
    activeIndex.value = index;
}

</script>

<style scoped>
.item {
    margin: 10px 25%;
    padding: 10px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    box-shadow: 3px 3px 10px -5px black;
    border-radius: 3px;
    /* border: 1px solid black; */
    cursor: pointer;
    transition: all .5s linear 0s;
}

.sha {
    box-shadow: 3px 3px 15px 1px black !important;
}

.item-left {
    width: 100px;
    height: 100px;
    border-radius: 3px;
}

.item-left img {
    width: 100%;
    height: 100%;
    object-fit: contain;
}

.item-right {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    gap: 25px;
    align-items: flex-start;
}
</style>