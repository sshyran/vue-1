<template>
  <div style="align-self: stretch;">
    <div :class="['send', 'h3', `send__enabled__${!disabled}`]" @click="submit">
      <div class="send__text">
        <slot />
        <div class="send__text__icon">
          <icon-loading-2 v-if="loading" class="send__text__icon__spin" />
          <icon-paper-plane-2 v-else />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;531;600;700;800&display=swap");

.send {
  height: 100%;
  font-family: "Inter", sans-serif;
  min-height: 3em;
  background: rgb(247, 247, 247);
  align-items: center;
  justify-content: center;
  display: flex;
  border-radius: 0.5rem;
}
.send__text {
  margin: 0 2rem;
  white-space: nowrap;
  display: flex;
  align-items: center;
}
.send__text__icon {
  width: 1.25rem;
  height: 1.25rem;
  padding: 0.25rem;
}
.send__text__icon__spin {
  animation: spin 2.5s linear infinite;
}
.h3 {
  font-size: 0.875rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-weight: 700;
  user-select: none;
  display: flex;
  align-items: center;
}
.send__enabled__false .send__text {
  color: rgba(0, 0, 0, 0.25);
  cursor: not-allowed;
  fill: rgba(0, 0, 0, 0.25);
}
@keyframes spin {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>

<script>
import IconPaperPlane2 from "./IconPaperPlane2";
import IconLoading2 from "./IconLoading2";

export default {
  components: {
    IconPaperPlane2,
    IconLoading2,
  },
  props: {
    disabled: {
      default: false,
    },
    loading: {
      default: false,
    },
  },
  methods: {
    submit() {
      this.$emit("click", true);
    },
  },
};
</script>
