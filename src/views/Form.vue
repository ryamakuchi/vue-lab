<template>
  <div class="form">
    <h1>フォームの実装</h1>

    <el-row :gutter="20">
      <el-col :span="12">
        <h2>フォーム</h2>

        <el-form ref="form" :model="request" label-width="120px">
          <el-form-item label="タイトル">
            <el-input v-model="request.title"></el-input>
          </el-form-item>

          <el-form-item label="種別">
            <el-select v-model="request.type" placeholder="選択して下さい">
              <el-option label="課題" value="issue"></el-option>
              <el-option label="バックログ" value="backlog"></el-option>
            </el-select>
          </el-form-item>

          <el-form-item label="本番環境">
            <el-switch v-model="request.isProduction"></el-switch>
          </el-form-item>

          <el-form-item label="内容">
            <el-input
              type="textarea"
              rows="3"
              v-model="request.desc"
            ></el-input>
          </el-form-item>

          <el-form-item>
            <el-button type="primary" @click="onSubmit">登録</el-button>
          </el-form-item>
        </el-form>
      </el-col>

      <el-col :span="6" :offset="2">
        <h2>プレビュー</h2>
        <ul>
          <li>タイトル: {{ request.title }}</li>
          <li>種別: {{ request.type }}</li>
          <li>本番環境: {{ request.isProduction }}</li>
          <li>内容: {{ request.desc }}</li>
        </ul>
      </el-col>
    </el-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

// RequestFormクラスの定義
class RequestForm {
  title: string = ''
  type: string = ''
  isProduction: boolean = false;
  desc: string = ''
}

// Form画面のビューモデル
export default Vue.extend({
  data() {
    return {
      request: new RequestForm()
    };
  },
  methods: {
    onSubmit(): void {
      alert("登録しました");
      this.request = new RequestForm();
    }
  }
});
</script>

<style scoped>
.el-form {
  width: 100%;
}
.el-select {
  width: 100%;
}
</style>