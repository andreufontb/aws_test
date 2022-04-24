<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
// import CommunityIcon from "./icons/IconCommunity.vue";
import { ref } from "vue";
// reactive state
const reversedText = ref("");
const inputText = ref("");

// functions that mutate state and trigger updates
function sendToLambaReverse() {
  // https://rb36f1bdm8.execute-api.us-east-1.amazonaws.com/default/reverseText
  reversedText.value = inputText.value;
}
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Input text</template>

    <input type="text" v-model="inputText" />
    <button @click="sendToLambaReverse">Submit</button>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Result</template>

    <p>{{ reversedText }}&nbsp;</p>
  </WelcomeItem>

  <!-- <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>History from S3</template>

    There is no history yet.
  </WelcomeItem> -->
</template>
