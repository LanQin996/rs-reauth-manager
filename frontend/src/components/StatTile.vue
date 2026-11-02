<script setup lang="ts">
import type { Component } from 'vue'
import { ZCard } from '@codex-proxy/ui/card'
defineProps<{ label: string; value: number; caption: string; tone: 'default' | 'info' | 'success' | 'warning' | 'danger'; icon: Component; pressed: boolean; hint: string }>()
defineEmits<{ select: [] }>()
</script>
<template>
  <div class="stat-wrap" role="button" tabindex="0" :aria-pressed="pressed" :aria-label="hint" :title="hint" @click="$emit('select')" @keydown.enter.prevent="$emit('select')" @keydown.space.prevent="$emit('select')">
    <ZCard as="div" padding="compact" class="stat" :class="`tone-${tone}`">
      <div class="stat-head"><span class="stat-label">{{ label }}</span><span class="stat-icon"><component :is="icon" :size="16" /></span></div>
      <strong class="stat-value">{{ value }}</strong>
      <span class="stat-caption">{{ caption }}</span>
    </ZCard>
  </div>
</template>
