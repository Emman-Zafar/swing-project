<template>
  <div id="folder-nav-title">
    <div class="fname">
      <div class="icon image" @click="$router.push({ name: Routes.folder, params: { path: '$home' } })"></div>
      <BreadCrumbNav :sub-paths="subPaths" @navigate="navigate" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";

import { subPath } from "@/interfaces";
import { Routes } from "@/router";

import BreadCrumbNav from "@/components/FolderView/BreadCrumbNav.vue";

const router = useRouter();

defineProps<{
  subPaths: subPath[];
}>();

function navigate(path: string) {
  router.push({ name: Routes.folder, params: { path } });
}
</script>

<style lang="scss">
#folder-nav-title {
  width: fit-content;
  display: grid;
  overflow: hidden;

  .fname {
    background-color: $gray4;
    border-radius: $small;
    height: 2.188rem;
    display: flex;
    align-items: center;
    max-width: 100%;
    overflow-x: auto;
    overflow-y: hidden;
    scrollbar-width: none;

    &::-webkit-scrollbar {
      display: none;
    }

    .icon {
      height: 2rem;
      aspect-ratio: 1;
      background-image: url("../../../assets/icons/folder.fill.svg");
      background-size: 1.5rem;
      margin-left: $smaller;
    }
  }
}
</style>
