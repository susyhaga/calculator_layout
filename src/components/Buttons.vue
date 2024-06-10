<script setup>
const props = defineProps({
    calculate: Function
});
</script>
<template>
    <div class="buttons">
        <div class="group">
            <input type="reset" class="button" @click="props.calculate('AC', 'ac')" name="ac" value="AC" />
            <input type="button" class="button" @click="props.calculate('÷', 'operator')" name="divide" value="÷" />
        </div>
        <div class="group">
            <input type="button" class="button" @click="props.calculate(7, 'number')" name="7" value="7" />
            <input type="button" class="button" @click="props.calculate(8, 'number')" name="8" value="8" />
            <input type="button" class="button" @click="props.calculate(9, 'number')" name="9" value="9" />
            <input type="button" class="button" @click="props.calculate('x', 'operator')" name="multiplication" value="x" />
        </div>
        <div class="group">
            <input type="button" class="button" @click="props.calculate(4, 'number')" name="number_4" value="4" />
            <input type="button" class="button" @click="props.calculate(5, 'number')" name="number_5" value="5" />
            <input type="button" class="button" @click="props.calculate(6, 'number')" name="number_6" value="6" />
            <input type="button" class="button" @click="props.calculate('-', 'operator')" name="-" value="-" />
        </div>
        <div class="group">
            <input type="button" class="button" @click="props.calculate(1, 'number')" name="1" value="1" />
            <input type="button" class="button" @click="props.calculate(2, 'number')" name="2" value="2" />
            <input type="button" class="button" @click="props.calculate(3, 'number')" name="3" value="3" />
            <input type="button" class="button" @click="props.calculate('+', 'operator')" name="+" value="+" />
        </div>
        <div class="group">
        <input type="button" class="button-center" @click="props.calculate(0, 'number')" name="0" value="0" />
        <input type="button" class="button" @click="props.calculate('.', 'number')" name="." value="." />
        <input type="button" class="button-center" @click="props.calculate('=', '=')" name="=" value="=" />
        </div>
    </div>
</template>

<style scoped>
.button {
    width: 60px;
    height: 50px;
    margin: 5px;
    padding: 2px;
    background: rgba(228, 222, 222, 0.4);
    border: 1px solid rgba(228, 222, 222, 0.4);
}

.button-center {
    width: 95px;
    height: 50px;
    margin: 5px;
    background: rgba(228, 222, 222, 0.4);
    border: 1px solid rgba(228, 222, 222, 0.4);
}

.button:hover {
    background-color: rgba(94, 100, 187, 0.74);
    border: none;
}
</style>