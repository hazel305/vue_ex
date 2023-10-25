<script>
export default {
  data() {
    return {
      message: "",
      multiple: "",
      checked: true,
      checkedNames: [],
      picked: "One",
      selected: "",
      options: [
        { text: "하나옵션", value: "1" },
        { text: "둘옵션", value: "2" },
        { text: "셋옵션", value: "3" },
      ],
      toggle: false,
      pick: "",
      msg: "",
    };
  },
};
</script>

<template>
  <div class="layout">
    <h1>This is an form input binding page</h1>

    <h2>텍스트</h2>
    <!-- <input
      type="text"
      :value="message"
      @input="(event) => (message = event.target.value)"
    /> -->
    <!-- 한국어 영어 중국어 다있으면 위와 같이 써야 한다! -->
    <input v-model="message" />
    <p>메세지:{{ message }}</p>
    <hr />
    <span>여러 줄 메세지:</span>
    <p style="white-space: pre-line">{{ multiple }}</p>
    <textarea
      v-model="multiple"
      placeholder="여러 줄을 추가해보세요"
    ></textarea>
    <hr />
    <h2>체크박스</h2>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>

    <span>배열 또는 set에 여러개의 체크박스 값을 바인딩</span>
    <div>체크된 이름: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="젝" v-model="checkedNames" />
    <label for="jack">잭</label>

    <input type="checkbox" id="john" value="존" v-model="checkedNames" />
    <label for="john">존</label>

    <input type="checkbox" id="mike" value="마이크" v-model="checkedNames" />
    <label for="mike">마이크</label>

    <h3>라디오</h3>
    <div>선택한 것: {{ picked }}</div>

    <input type="radio" id="one" value="하나" v-model="picked" />
    <label for="one">하나</label>

    <input type="radio" id="two" value="둘" v-model="picked" />
    <label for="two">둘</label>

    <h3>셀렉트</h3>
    <div>선택됨: {{ selected }}</div>

    <select v-model="selected">
      <option disabled value="">다음 중 하나를 선택하세요</option>
      <option>곰팅이</option>
      <option>곰돌이</option>
      <option>곰곰이</option>
    </select>
    <br />
    <h2>셀렉트 옵션은 v-for로 동적으로 렌더링</h2>
    <select v-model="selected">
      <option v-for="option in options" :value="option.value" :key="option">
        {{ option.text }}
      </option>
    </select>

    <div>선택됨: {{ selected }}</div>
    <hr />
    <h2>값 바인딩 하기</h2>
    <!-- `picked`는 선택 시 문자열 "가"입니다. -->
    <input type="radio" v-model="picked" value="가" />

    <!-- `toggle`은 true 또는 false입니다. -->
    <input type="checkbox" v-model="toggle" />

    <!-- `selected`는 첫 번째 옵션이 선택될 때 문자열 "한글"입니다. -->
    <select v-model="selected">
      <option value="한글">한글</option>
    </select>
    <hr />
    <input
      type="checkbox"
      v-model="toggle"
      true-value="toggle"
      false-value="toggle"
    />

    <hr />
    <div>선택한 것: {{ pick }}</div>
    <input type="radio" v-model="pick" :value="'first'" />
    <input type="radio" v-model="pick" :value="'second'" />

    <hr />
    <h2>수식어</h2>
    <h3>.lazy - 입력하고 나서 밖에 클릭해야 이벤트가 실행되면서 출력됨</h3>
    <!-- "input" 대신 "change" 이벤트 후에 동기화됨 -->
    <input v-model="msg" /><!--input-->
    <input v-model.lazy="msg" /><!--change-->
    {{ msg }}
  </div>
</template>

<style>
.box {
  border: 1px solid;
  padding: 20px;
  display: inline-block;
}
@media (min-width: 1024px) {
  .layout {
    padding: 30px 10px;
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
