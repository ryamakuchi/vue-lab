<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld :msg="message"/>

    <h3>リストレンダリング</h3>
    <ul id="item-list">
      <li v-for="item in items" :key="item.id">
        {{item.name}}
      </li>
    </ul>

    <h3>イベントハンドリング</h3>
    <el-button @click="onClick">onClick</el-button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

// ここにインターフェースを追加
declare interface Item {
  id: number;
  name: string;
}

export default Vue.extend({
  name: 'home',
  components: {
    HelloWorld,
  },
  data() {
    return {
      message: 'Hello Vue.js!',
      items: [
        {
          id: 1,
          name: "キーボード"
        },
        {
          id: 2,
          name: "マウス"
        }
      ] as Item[]
    }
  },
  methods: {
    onClick(): void {
      alert(this.message);
    }
  }
});
</script>
