<template>
  <div
    class="flex w-full pl-4 pr-2 py-2 h-14 justify-between items-center border-b border-slate-50 dark:border-slate-800/50"
  >
    <div class="flex items-center gap-1.5">
      <h1 class="font-medium text-slate-900 dark:text-slate-25 text-xl">
        {{ $t('INBOX.LIST.TITLE') }}
      </h1>
      <div
        role="button"
        class="flex gap-1 items-center py-1 px-2 border border-slate-100 dark:border-slate-700/50 rounded-md"
        @click="openInboxDisplayMenu"
      >
        <span
          class="text-slate-600 relative -top-px dark:text-slate-200 text-xs text-center font-medium"
        >
          {{ $t('INBOX.LIST.DISPLAY_DROPDOWN') }}
        </span>
        <fluent-icon
          icon="chevron-down"
          size="12"
          class="text-slate-600 dark:text-slate-200"
        />
      </div>
    </div>
    <div class="flex relative gap-1 items-center">
      <!-- <woot-button
        variant="clear"
        size="small"
        color-scheme="secondary"
        icon="filter"
        @click="openInboxFilter"
      /> -->
      <woot-button
        variant="clear"
        size="small"
        color-scheme="secondary"
        icon="mail-inbox"
        @click="openInboxOptionsMenu"
      />
      <inbox-option-menu
        v-if="showInboxOptionMenu"
        v-on-clickaway="openInboxOptionsMenu"
        class="absolute top-9"
      />
    </div>
  </div>
</template>

<script>
import { mixin as clickaway } from 'vue-clickaway';
import InboxOptionMenu from './InboxOptionMenu.vue';
export default {
  components: {
    InboxOptionMenu,
  },
  mixins: [clickaway],
  data() {
    return {
      showInboxOptionMenu: false,
    };
  },
  methods: {
    openInboxDisplayMenu() {
      this.$emit('open-display-menu');
    },
    openInboxOptionsMenu() {
      this.showInboxOptionMenu = !this.showInboxOptionMenu;
    },
  },
};
</script>

<style></style>