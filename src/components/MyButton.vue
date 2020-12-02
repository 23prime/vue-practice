<template>
    <button @click="onClick"><slot></slot></button>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from "vue-property-decorator";

@Component
export default class MyButton extends Vue {
    private count = 0;

    @Prop()
    private greet?: string;

    @Emit("click")
    // eslint-disable-next-line @typescript-eslint/no-empty-function, @typescript-eslint/no-unused-vars
    private click(count: number) {}

    private onClick() {
        alert(this.greet);
        this.count++;
        this.click(this.count);
    }
}
</script>
