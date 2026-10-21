<template>
    <div class="cart-list">
        <div class="list" v-for="(item, index) in items" :key="index">
            <div class="act-list">
                <div class="detail">
                    <input type="radio" @click="sendClick">
                    <span>{{ item }}</span>
                </div>
                <span class="btn-delete" @click="emit('remove', index)">🗑️</span>
            </div>
            <hr>
        </div>
        <div class="clear">
            <button class="btn-clear-all" @click="emit('clear')">🧹Clear All</button>
        </div>
    </div>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue';
defineProps({
    items: Array
})
const emit = defineEmits(['remove', 'clear'])
</script>

<style scoped>
.cart-list {
    background-color: antiquewhite;
    max-width: auto;
    border: none;
    border-radius: 8px;
    padding: 10px;
}

.act-list {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.detail {
    display: flex;
    align-items: center;
    gap: 10px;
}

.btn-delete {
    font-size: small;
    filter: sepia(1) saturate(100) hue-rotate(330deg);
}

.clear {
    display: flex;
    justify-content: end;

}

.btn-clear-all {

    background-color: antiquewhite;
    color: red;
    border: 1px solid red;
    padding: 4px 24px;

    border-radius: 8px;

}
</style>