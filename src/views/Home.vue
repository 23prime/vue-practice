<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />

        <p>{{ greetText }}</p>
        <p>{{ count }} 回目の挨拶</p>
        <p v-if="isRegular">まいど〜ｗ</p>
        <p>
            <MyButton class="my-button" :greet="greetText" @click="onMyButtonClicked">
                Greet
            </MyButton>
        </p>

        <p>
            <ResetButton v-model="greetText">
                Reset
            </ResetButton>
        </p>
    </div>
</template>

<style scoped>
.my-button {
    color: brown;
}
</style>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

@Component({
    components: {
        HelloWorld,
        MyButton,
        ResetButton,
    },
})
export default class Home extends Vue {
    private count = 0;
    private greetText = "Hello!";

    private get isRegular(): boolean {
        return this.count > 4;
    }

    @Watch("count") // this.count ではダメ
    private countChanged() {
        if (this.count === 5) {
            alert("常連になりました。");
        }
    }

    private onMyButtonClicked(count: number) {
        this.count = count;
        this.greetText = "こん";
    }
}
</script>
