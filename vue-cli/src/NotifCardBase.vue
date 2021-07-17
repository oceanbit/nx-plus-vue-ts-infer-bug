<template>
  <!-- This card is just the width + padding + the shadow -->
  <div class="notif-card-base-container">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent, watch, PropType } from 'vue';

export default defineComponent({
  name: 'NotifCardBase',
  props: {
    soundUrl: {
      type: String
    },
    index: {
      type: Number,
      required: true,
    },
  },
  emits: ['soundend'],
  setup(props, {emit}) {
    watch(() => props.index, () => {
      if (props.index !== 0 || !props.soundUrl) {
        return;
      }

      function test(val: string) {return val};

      test(props.soundUrl);
    }, {
      immediate: true
    });
  }
})
</script>

<style scoped>
.notif-card-base-container {
  padding: 24px;
  width: 400px;
  background: var(--surface);
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.16), 0px 12px 24px rgba(0, 0, 0, 0.12);
  border-radius: 16px;
}
</style>
