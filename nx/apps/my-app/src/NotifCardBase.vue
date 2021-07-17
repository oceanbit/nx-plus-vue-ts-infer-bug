<template>
  <div></div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'NotifCardBase',
  props: {
    soundUrl: {
      type: String
    },
  },
  setup(props) {
    function test(val: string) {return val};

    test(props.soundUrl);
  }
})
</script>
