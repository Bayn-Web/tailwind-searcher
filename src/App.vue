<template>
  <div class="h-screen">
    <div class="space-x-3 flex justify-center">
      <a-select @change="keyChange" show-search :options="optionsList" :field-names="{ label: 'label', value: 'value' }"
        :filter-option="filterOption" v-model:value="selectedValue" class="w-[300px]" />
      <a-select @change="valueChange" show-search :options="optionsList" :field-names="{ label: 'value', value: 'label' }"
        :filter-option="filterOption" v-model:value="selectedKey" class="w-[300px]" />
      <a-button :disabled="selectedValue == undefined" @click="addClassName">→</a-button>
    </div>
    <a-list bordered :grid="{ column: 6 }" size="small" :data-source="classNameList">
      <template #renderItem="{ item }">
        <a-list-item class="w-fit p-2 m-2 space-x-4 ring rounded border" align="center">
          <a-tag class="cursor-default" color="green">{{ item.label }}</a-tag>
          <a-button danger rounded class="scale-150" type="link" @click="remove(item)">×</a-button>
        </a-list-item>
      </template>
    </a-list>
    <SandBox :classNames="classNameList"></SandBox>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import SandBox from './components/SandBox.vue';
import json from "./data.json"

let jsonwithkey = json.map((item) => {
  return {
    label: item.value,
    value: item.label,
    key: item.label
  }
})
const optionsList = ref(jsonwithkey)
const selectedKey = ref();
const selectedValue = ref();
const classNameList = ref<{ value: string, label: string, id: number }[]>([])
const filterOption = (input: string, option: any) => {
  return option.value.toLowerCase().indexOf(input.toLowerCase()) >= 0;
};

const keyChange = (_value: string, e: { value: string, label: string }) => {
  selectedKey.value = e.label;
}

const valueChange = (_value: string, e: { value: string, label: string }) => {
  selectedValue.value = e.value;
}
let id = 0
const addClassName = () => {
  classNameList.value.push({ label: selectedKey.value, value: selectedValue.value, id: id++ });
}

const remove = (item: { label: string, value: string, id: number }) => {
  let f = true
  classNameList.value = classNameList.value.filter((value) => {
    if (value.id !== item.id) {
      return true
    }
  })
}
</script>

<style scoped></style>
