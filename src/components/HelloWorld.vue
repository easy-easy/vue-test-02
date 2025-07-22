<script setup lang="ts">
import { computed, ref } from "vue";

defineProps<{ msg: string }>();

const count = ref(0);
const count2 = computed(() => count.value + 1);

console.log("HelloWorld component rendered");

let count3 = 0;
const incrementCount3 = () => {
  count3++;
  console.log("incrementCount3 called");
};

// 判定結果を一時的に保持するref
const lastIsOdd = ref<boolean>(true)

// 純粋関数: 今の秒が奇数か判定
const isOddNow = () => new Date().getSeconds() % 2 === 1

// ボタン押下時に判定して結果を更新
const checkIsOdd = () => {
  lastIsOdd.value = isOddNow()
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <button type="button" @click="incrementCount3">
      count3 is {{ count3 }}
    </button>
    <p>now is odd: {{ lastIsOdd? "yes" : "no" }}</p>
    <button type="button" @click="checkIsOdd">
      Check if now is odd
    </button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Learn more about IDE Support for Vue in the
    <a
      href="https://vuejs.org/guide/scaling-up/tooling.html#ide-support"
      target="_blank"
      >Vue Docs Scaling up Guide</a
    >.
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
