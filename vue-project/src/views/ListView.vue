<script>
// const awesome = true;

export default {
  data() {
    return {
      ParentLangs: "Web",
      items: [
        { id: 1, title: "HTML", desc: "HTML is..." },
        { id: 2, title: "CSS", desc: "CSS is..." },
        { id: 3, title: "JS", desc: "JS is..." },
      ],
      myObject: {
        title: "Vue에서 목록을 작성하는 방법",
        author: "홍길동",
        publishedAt: "2016-04-10",
      },
      numbers: [1, 2, 3, 4, 5],
      sets: [
        [1, 2, 3, 4, 5],
        [6, 7, 8, 9, 10],
      ],
    };
  },
  computed: {
    evenNumbers() {
      console.log("evenNumbers 실행!");
      //numbers의 값이 변경될때만 실행
      return this.numbers.filter((n) => n % 2 === 0);
    },
  },
  methods: {
    even(numbers) {
      console.log("even 실행!");
      //인수 numbers의 값을 가지고 직접 바뀌지 않으면 sets값이 바뀌는거에 상관없이
      //data 함수내 어느값이든 변경되면 실행
      return numbers.filter((number) => number % 2 === 0);
    },
  },
};
</script>

<template>
  <div class="layout">
    <h1>This is list Rendering page</h1>

    <ul>
      <li v-for="(item, index) in items" :key="item.id">
        {{ index }} / {{ item.title }}
      </li>
    </ul>
    <ul>
      <li v-for="value in myObject" :key="value.id">
        {{ value }}
      </li>
    </ul>
    <span v-for="n in 10" :key="n">{{ n }}</span>

    <ul>
      <hr />
      <template v-for="item in items" :key="item.id">
        <li>{{ item.desc }}</li>
      </template>
    </ul>

    <hr />
    <h3>필터링/정렬 결과 표시</h3>
    <ul>
      <li v-for="n in evenNumbers" :key="n.id">{{ n }}</li>
    </ul>
    <ul v-for="numbers in sets" :key="numbers">
      <li v-for="n in even(numbers)" :key="n">{{ n }}</li>
    </ul>
    <button @click="sets[0].push(2)">add</button>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .layout {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
