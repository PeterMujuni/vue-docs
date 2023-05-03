<template>
    <button @click="increment">{{ text }} {{ count }}</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

    export default defineComponent({
        name: "ButtonComponent",
        props: {
            text: String,
        },
        data() {
            return {
                count: 0
            }
        },
        methods: {
            increment() {
                this.count++
            }
        }
    })
</script>