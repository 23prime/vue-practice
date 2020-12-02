<template>
    <button @click="onClick"><slot></slot></button>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from "vue-property-decorator";

@Component
export default class extends Vue {
    private initialValue!: string;

    // 生成時に呼ばれるメソッド
    private created() {
        // 生成時に親コンポーネント Home から初期値を受け取る
        this.initialValue = this.value;
    }

    // v-model に対するゲッター的なプロパティ
    @Prop()
    private value!: string;

    // v-model に対するセッター的なイベント
    @Emit()
    // eslint-disable-next-line @typescript-eslint/no-empty-function, @typescript-eslint/no-unused-vars
    private input(value: string) {}

    private onClick() {
        this.input(this.initialValue);
    }
}
</script>
