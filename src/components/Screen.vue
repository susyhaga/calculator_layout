<script setup>
    import { computed } from 'vue';

    const props = defineProps({
        result: String,
        num1: String,
        operator: String,
        num2: String,
    });

    const displayValue = computed(() => {
        return props.result !== '' ? props.result : `${props.num1} ${props.operator} ${props.num2}`;
    });

//  Se estado.result não estiver vazio, ele exibe o resultado da operação.
// Caso contrário, ele exibe a operação atual composta por estado.num1, estado.operator e estado.num2. 
</script>

<template>
    <input
        type="text"
        class="screen"
        :value="displayValue"
        disabled
    />
</template>
<style scoped>
.screen {
    padding: 10px;
    margin: 10px;
    font-size: 21px;
    text-align: right;
    border: solid 1px #000;
    box-shadow: 1px 1px 1px #000;
}
</style>