<template>
  <aside class="sider" :class="{ collapsed: isCollapsed }">
    <slot />

    <div class="trigger" @click="isCollapsed ? openSider() : closeSider()">
      <img :src="IconRight" class="icon-right" alt="arrow" />
    </div>
  </aside>
</template>

<script lang="ts" setup>
import IconRight from '@/assets/icons/icon-right.svg'
import { useSider } from '@/hooks'

const { isCollapsed, openSider, closeSider } = useSider()
</script>

<style lang="scss" scoped>
.sider {
  position: fixed;
  top: 0;
  right: 0;
  z-index: 200;
  height: 100%;
  transition: transform 0.2s;

  .icon-right {
    transition: transform 0.2s;
  }

  &.collapsed {
    transform: translateX(100%);

    .icon-right {
      transform: rotateY(-180deg);
    }
  }

  .trigger {
    position: absolute;
    top: 50%;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 1.2rem;
    height: 4rem;
    background-color: lighten($color-configurator, 2);
    border-radius: 0.4rem 0 0 0.4rem;
    transform: translate(-100%, -50%);
    cursor: pointer;
    transition: width 0.2s, background-color 0.2s;

    &:hover {
      width: 1.5rem;
      background-color: lighten($color-configurator, 5);
    }
  }
}
</style>
