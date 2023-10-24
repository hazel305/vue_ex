<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
  msg2: {
    type: String,
    required: true,
  },
});

const rawHtml = '<a href="">Link</a>';
const pid = 10;
const isButtonDisabled = true;
const objectOfAttrs = {
  id: "container",
  class: "wrapper",
};

const number = 20;
const ok = false;
const message = "안녕하세요";
const id = 30;

const sayHello = (msg) => {
  alert(msg);
};

const url = "https://www.google.com";

const attributeName = "href";

const items = [
  { id: 0, title: "html" },
  { id: 1, title: "css" },
  { id: 2, title: "js" },
];

const onSubmit = () => {
  alert("제출되었습니다.");
};
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h1 class="green">{{ msg2 }}</h1>

    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <hr />
    <p>{{ rawHtml }}</p>
    <p><span v-html="rawHtml"></span></p>

    <hr />
    <h2>속성 바인딩</h2>
    <div v-bind:id="pid"></div>
    <div :id="pid"></div>
    <div id="pid"></div>
    <div id="{{pid}}"></div>
    <div id="pid">{{ pid }}</div>

    <h2>블리언 바인딩</h2>
    <button :disabled="isButtonDisabled">버튼</button>
    <button :disabled="!isButtonDisabled">버튼</button>
    <h2>여러속성 바인딩</h2>
    <div v-bind="objectOfAttrs"></div>
    <h2>js expression</h2>

    {{ number + 1 }}
    {{ ok ? "예" : "아니오" }}
    {{ message.split("").reverse().join("") }}
    <div :id="`list-${id}`"></div>

    <h2>함수호출</h2>
    <!-- <span :title="sayHello('안녕')"></span> -->
    <!-- {{ sayHello("안녕하세요!") }} -->

    <h2>디렉티브</h2>
    <a v-bind:href="url">구글</a>
    <a :href="url">구글</a>
    <a v-bind:[attributeName]="url"> 구글 </a>

    <div v-for="item in items" :key="item.id">
      {{ item.title }}
    </div>

    <h2>v-on</h2>
    <div>
      <button type="button" v-on:click="sayHello('hello')">hello</button>
      <button @click="sayHello('안녕')">안녕</button>
      <button @mouseover="sayHello('hola')">hola</button>

      <h3>form submit</h3>
      <form action="" @submit.prevent="onSubmit">
        <button>제출</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
D h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
