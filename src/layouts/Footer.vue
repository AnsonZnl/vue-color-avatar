<template>
  <footer class="footer">
    <div>
      Made by
      <a
        class="link"
        href="https://leoku.top"
        target="_blank"
        rel="nofollow noopener noreferrer"
      >
        LeoKu
      </a>
    </div>

    <div class="divider">|</div>

    <div class="locale" @click="switchLocale">
      {{ locale === Locale.EN ? '简体中文' : 'English' }}
    </div>
  </footer>
</template>

<script lang="ts" setup>
import { useI18n } from 'vue-i18n'

import { Locale } from '@/enums'

const { locale } = useI18n()

function switchLocale() {
  locale.value = locale.value === Locale.EN ? Locale.ZH : Locale.EN
}
</script>

<style lang="scss" scoped>
.footer {
  display: flex;
  align-items: center;
  justify-content: center;
  height: $layout-footer-height;
  padding: 0.8rem 0;
  color: rgba($color-text, 0.4);
  font-weight: bold;
  font-size: 0.8rem;

  .divider {
    padding: 0 1rem;
  }

  .locale {
    cursor: pointer;
  }

  .link,
  .locale {
    transition: color 0.2s;

    &:hover {
      color: $color-text;
    }
  }
}
</style>
