<template>
  <div>
      <div class="box">
        <div
          class="s-captcha"
          :data-prop-sitekey="SCAPTCHA_ONCOMPLETE_SITEKEY"
          :data-prop-oncomplete="SCAPTCHA_ONCOMPLETE_PROP"
        />
      </div>
  </div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';

export default {
  setup() {
    const SCAPTCHA_ONCOMPLETE_SITEKEY = 'c18e029759b44b499a0bd4f0dcb65ee8';
    const SCAPTCHA_ONCOMPLETE_PROP = 'SCAPTCHA_ONCOMPLETE';

    onMounted(() => {
      // Код для инициализации scaptcha
      const script = document.createElement('script');
      script.async = true;
      script.src = 'https://api.scaptcha.com/widget/scaptcha-ui.js';
      document.head.appendChild(script);

      // Опционально, удалить скрипт при размонтировании компонента
      onBeforeUnmount(() => {
        document.head.removeChild(script);
      });
    });

    return {
      SCAPTCHA_ONCOMPLETE_SITEKEY,
      SCAPTCHA_ONCOMPLETE_PROP,
    };
  },
};
</script>

<style scoped>
/* Ваши стили здесь */
.box {
  display: flex;
  justify-content: center;
}
</style>
