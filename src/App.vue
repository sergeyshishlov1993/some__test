<template>
  <div class="container">
    <the-form @submit.prevent="createPost">
      <ui-title-form>создать пост</ui-title-form>

      <ui-input
        :placeholder="'описание'"
        UiButtonForm
        :value="id"
        @getInputValue="addId"
      ></ui-input>

      <ui-input
        :placeholder="'название'"
        :value="title"
        @getInputValue="addTitle"
      ></ui-input>

      <ui-button-form>создать</ui-button-form>
    </the-form>

    <div v-if="isFilled">
      <the-post v-for="(item, index) in arr" :key="item.id">
        <div>
          <ui-item-post>{{ item.id }} :</ui-item-post>
          <ui-item-post> {{ item.title }}</ui-item-post>
        </div>
        <ui-button-post @click="delPost(index)">Удалить</ui-button-post>
      </the-post>
    </div>

    <the-alarm v-else>
      <ui-title-alarm>вы не можете отправить пустой пост</ui-title-alarm>
      <ui-button-post @click="isFilled = !isFilled"> закрыть</ui-button-post>
    </the-alarm>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import TheForm from "@/components/UiForm.vue";
import ThePost from "./components/ThePost.vue";
import UiTitleForm from "@/components/UiTitleForm.vue";
import UiInput from "./components/UiInput.vue";
import UiButtonForm from "./components/UiButtonForm.vue";
import UiItemPost from "@/components/UiItemPost.vue";
import UiButtonPost from "./components/UiButtonPost.vue";
import TheAlarm from "@/components/TheAlarm.vue";
import UiTitleAlarm from "./components/UiTitleAlarm.vue";

let id = ref("");
let title = ref("");
let isFilled = ref(true);

const arr = reactive([
  {
    id: "some id",
    title: "some title",
  },
]);

function addId(event) {
  return (id.value = event);
}

function addTitle(event) {
  return (title.value = event);
}

function createPost() {
  const newObj = reactive({
    id: id.value,
    title: title.value,
  });
  id.value = "";
  title.value = "";
  if (!newObj.id || !newObj.title) {
    isFilled.value = false;
  } else {
    return arr.push(newObj);
  }
}

function delPost(index) {
  if (arr.indexOf(index)) {
    return arr.splice(index, 1);
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  padding: 50px;
}
</style>
