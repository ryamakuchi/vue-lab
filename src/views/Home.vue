<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld :msg="message"/>

    <h2>リストレンダリング</h2>
    <ul id="item-list">
      <li v-for="item in items" :key="item.id">
        {{item.name}}
      </li>
    </ul>

    <h2>イベントハンドリング</h2>
    <el-button @click="onClick">onClick</el-button>

    <h2>算出プロパティ</h2>
    <p>{{ computedMsg }}</p>

    <h2>条件付きレンダリング</h2>
    <el-button @click="showDetail">
      {{ detail ? '非表示' : '表示' }}
    </el-button>
    <div v-show="detail">
      詳細が表示されました。
    </div>

    <el-button @click="raiseError">
      {{ hasError ? 'エラー解除' : 'エラーを起こす' }}
    </el-button>
    <div
      class="el-alert is-light"
      :class="{ 'el-alert--error': hasError }">
      {{ hasError ? 'Error!!!' : 'no problem' }}
    </div>
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
      ] as Item[],
      detail: false,
      hasError: false
    }
  },
  computed: {
    computedMsg(): string {
      return this.message.replace(/!/g, "") + " + TypeScript!"
    }
  },
  methods: {
    onClick(): void {
      alert(this.message);
    },
    showDetail(): void {
      this.detail = !this.detail
    },
    raiseError(): void {
      this.hasError = !this.hasError
    }
  }
});
</script>
