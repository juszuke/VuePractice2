<template>
  <div>
    <div v-if="isScene1Active" class="scene1">
      <div class="head">
        <p>STEP1</p>
        <h2>お客様の情報を入力してください</h2>
      </div>
      <div class="main">
        <p>-性別-</p>
        <input type="radio" id="male" value="男性" v-model="gender">
        <label for="male">男性</label>
        <input type="radio" id="female" value="女性" v-model="gender">
        <label for="female">女性</label>
        <p>-生年月日-</p>
        <input type="date" v-model="dateOfBirth">
      </div>
      <div class="button">
        <input v-on:click="showScene2" type="button" value="次へ進む">
      </div>
    </div>

    <div v-if="isScene2Active" class="scene2 none">
      <div class="head">
        <p>STEP2</p>
        <h2>以下にお答えください</h2>
      </div>
      <div class="main">
        <div>
          <p>現在、生命保険に加入されていますか？</p>
          <input type="radio" id="yes" value="はい" v-model="q1">
          <label for="yes">はい</label>
          <input type="radio" id="no" value="いいえ" v-model="q1">
          <label for="no">いいえ</label>
        </div>
        <div v-if="q1">
          <p>現在入院中ですか？または、最近３ヶ月以内に医師の診察・検査の結果、入院・手術を勧められたことはありますか？</p>
          <input type="radio" id="yes" value="はい" v-model="q2">
          <label for="yes">はい</label>
          <input type="radio" id="no" value="いいえ" v-model="q2">
          <label for="no">いいえ</label>
        </div>
        <div v-if="q2">
          <p>過去５年以内に、病気やけがで、手術を受けたこことまたは継続して７日以上の入院をしたことがありますか？</p>
          <input type="radio" id="yes" value="はい" v-model="q3">
          <label for="yes">はい</label>
          <input type="radio" id="no" value="いいえ" v-model="q3">
          <label for="no">いいえ</label>
        </div>
      </div>
      <div class="button">
        <input v-on:click="showScene1" type="button" value="前へ戻る">
        <input v-on:click="showScene3" type="button" value="次へ進む">
      </div>
    </div>

    <div v-if="isScene3Active" class="scene3 none">
      <div class="head">
        <p>STEP3</p>
        <h2>ご相談内容をご記入ください</h2>
      </div>
      <div class="main">
        <div>
          <p>-ご相談内容-</p>
          <textarea v-model="q4"></textarea>
        </div>
      </div>
      <div class="button">
        <input v-on:click="showScene2" type="button" value="前へ戻る">
        <input type="button" value="次へ進む">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      gender: '',
      dateOfBirth: '',
      q1: '',
      q2: '',
      q3: '',
      q4: '',
      isScene1Active: true,
      isScene2Active: false,
      isScene3Active: false
    }
  },
  methods: {
    showScene1 () {
      this.isScene1Active = true
      this.isScene2Active = false
      this.isScene3Active = false
    },
    showScene2 () {
      this.isScene1Active = false
      this.isScene2Active = true
      this.isScene3Active = false
    },
    showScene3 () {
      this.isScene1Active = false
      this.isScene2Active = false
      this.isScene3Active = true
    }
  }
}
</script>
