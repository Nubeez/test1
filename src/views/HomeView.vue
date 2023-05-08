<template>
  <div class="home">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <!-- 모달창 -->
    <div class="black-bg" v-if="modal == true">
      <div class="white-bg">
        <img :src="item[0].image" style="width: 100%" />
        <h4>{{ item[active].title }}</h4>
        <p>{{ item[active].content }}</p>
        <p>{{ numberWithCommas(item[active].price) + "원" }}</p>
        <button @click="modal = false">닫기</button>
      </div>
    </div>
    <!-- 할인 창 -->
    <div>
      <DisCount />
    </div>
    <!-- 정렬 버튼 -->
    <div class="btn_wrap">
      <button>제목순</button>
      <button>낮은가격순</button>
      <button>높은가격순</button>
      <button>50만원이하</button>
      <button>되돌리기</button>
    </div>
    <!-- item 반복문 -->
    <div class="item_wrap">
      <ul class="item_list">
        <li v-for="item in item" :key="item.id">
          <img :src="item.image" alt="Room Image" />
          <h4
            @click="
              modal = true;
              active = item.id;
            "
          >
            {{ item.title }}
          </h4>
          <p>{{ numberWithCommas(item.price) + "원" }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
ul,
ol,
li {
  list-style: none;
  text-decoration: none;
}
/* 모달 css */
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.btn_wrap {
  display: flex;
  justify-content: flex-start;
}
.btn_wrap button {
  margin: 5px;
}
.item_wrap {
  display: flex;
  justify-content: center;
}
.item_list {
  cursor: pointer;
}
.item_list li {
  margin: 20px 0;
}
.item_list li img {
  width: 100%;
}
</style>
<script>
import item from "@/item.js";
import DisCount from "../components/DisCount.vue";

export default {
  name: "ItemList",
  components: {
    DisCount,
  },
  data() {
    return {
      item: item,
      modal: false,
      active: 0,
    };
  },
  methods: {
    numberWithCommas(value) {
      return value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
