<script setup lang="ts">
import { AlertTriangle, CircleCheck, Info, X } from '@lucide/vue'
import { ZIconButton } from '@codex-proxy/ui/icon-button'
defineProps<{ tone?: 'info' | 'success' | 'warning' | 'danger'; dismissible?: boolean }>()
defineEmits<{ dismiss: [] }>()
</script>
<template>
  <div class="notice" :class="`notice-${tone || 'info'}`">
    <CircleCheck v-if="tone === 'success'" :size="16" />
    <AlertTriangle v-else-if="tone === 'warning' || tone === 'danger'" :size="16" />
    <Info v-else :size="16" />
    <span class="notice-text"><slot /></span>
    <slot name="action" />
    <ZIconButton v-if="dismissible" size="small" title="关闭提示" aria-label="关闭提示" @click="$emit('dismiss')"><X :size="14" /></ZIconButton>
  </div>
</template>
