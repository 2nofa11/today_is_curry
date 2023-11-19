<script lang="ts">
import { ref, type PropType } from "vue";

export default {
  props: {
    messages: {
      required: true,
      type: Array as PropType<String[]>,
    },
  },
  setup(props) {
    function selectRandomMessage(): String {
      return props.messages[Math.floor(Math.random() * props.messages.length)];
    }

    const randomMessage = ref<String>(selectRandomMessage());
    function setGreeting() {
      randomMessage.value = selectRandomMessage();
    }

    // テンプレートや他の Options API フックを公開します
    return {
      randomMessage,
      setGreeting,
    };
  },
};
</script>

<template>
  <div>
    <h3>{{ randomMessage }}！ 訪問いただきありがとうございます！</h3>
    <button @click="setGreeting">新しい挨拶</button>
  </div>
</template>
