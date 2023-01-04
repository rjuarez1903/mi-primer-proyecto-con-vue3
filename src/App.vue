<script setup>
    import { ref, computed } from "vue"

    const heading = "Hola Vue JS"
    let numbers   = ref([])
    const count   = ref(0)

    const increment      = () => count.value++
    const decrement      = () => count.value--
    const reset          = () => count.value = 0
    const add            = () => numbers.value.push(count.value)
    const blockAddBtn    = () => numbers.value.includes(count.value)
    const classCount     = computed(() => {
        if (count.value == 0) {
          return 'zero'
        } else if (count.value > 0) {
          return 'positive'
        } else {
          return 'negative'
        }
    })
</script>

<template>
    <div class="container text-center mt-3">
        <h1>{{ heading }}</h1>
        <h2 :class="classCount">{{ count }}</h2>
        <div class="btn-group">
            <button @click="increment"  class="btn btn-success">Increment</button>
            <button @click="decrement" class="btn btn-danger">Decrement</button>
            <button @click="reset" class="btn btn-secondary">Reset</button>
            <button @click="add" :disabled="blockAddBtn()" class="btn btn-primary">Add</button>
        </div>
        <ul class="list-group mt-3">
            <li v-for="(num, index) in numbers" :key="index" class="list-group-item"> {{ num }} </li>
        </ul>
    </div>
</template>

<style>
    h1 {
        color: darkcyan;
    }
    .positive {
        color: green;
    }

    .negative {
        color:red
    }

    .zero {
        color: peru;
    }
</style>